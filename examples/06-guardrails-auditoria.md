# Exemplo do Dominio 6 - Guardrails e registro de auditoria

## Problema

Um agente pode ler o repositorio, propor mudancas e executar validacoes. O sistema precisa limitar seu impacto e explicar cada tentativa permitida, bloqueada ou escalada.

## Matriz de controle

| Acao | Nivel de autonomia | Controle preventivo | Evidencia |
| --- | --- | --- | --- |
| Ler codigo e issues | Somente leitura | Token com permissao de leitura. | Log de ferramenta. |
| Editar `src/` e `tests/` | Propor | Branch isolada e caminhos permitidos. | Diff e commits. |
| Executar testes aprovados | Executar com guardrails | Lista de comandos, timeout e ambiente isolado. | Check e log. |
| Alterar workflows ou infraestrutura | Autorizacao humana | CODEOWNERS e ruleset. | Revisao e aprovacao na PR. |
| Fazer deploy em producao | Autorizacao humana | Environment protegido e credencial fora do agente. | Registro do deployment. |
| Ler secrets ou fazer push direto em `main` | Proibido | Permissoes negadas pela plataforma. | Evento de bloqueio. |

## Evento de auditoria

```json
{
  "timestamp": "2026-09-22T14:30:00-03:00",
  "actor": "implementation-agent",
  "task": "issue-42",
  "action": "edit-file",
  "target": ".github/workflows/deploy.yml",
  "decision": "blocked",
  "policy": "allowed-paths-v1",
  "reason": "target outside src/ and tests/",
  "head_sha": "abc1234",
  "correlation_id": "run-9002"
}
```

O registro nao deve conter secrets, tokens, prompts com dados pessoais ou conteudo sensivel desnecessario.

## Como executar o exercicio

1. Escolha uma acao da matriz e identifique seu nivel de autonomia.
2. Simule a tentativa usando um alvo permitido e produza um evento com decisao `allowed`.
3. Troque o alvo para `.github/workflows/deploy.yml` e produza o evento bloqueado acima.
4. Confirme que ambos os eventos permitem responder quem, quando, o que, por que e em qual execucao.
5. Simule duas repeticoes do bloqueio e registre a escalacao, sem conceder permissao adicional automaticamente.

## O que observar

- O guardrail age antes ou durante a operacao; uma instrucao escrita sem enforcement nao seria suficiente.
- O agente nao recebe a credencial que protege a acao de maior impacto.
- O evento explica a decisao sem expor informacao sensivel.
- Repetir uma operacao proibida nao transforma a falha em transitoria.

## Riscos e mitigacoes

| Risco | Mitigacao |
| --- | --- |
| Token com privilegio excessivo | Menor privilegio por job e credenciais separadas. |
| Bypass pelo administrador | Aplicar regras aos papeis relevantes e auditar excecoes. |
| Logs sem contexto | Usar task, SHA, politica e correlation ID. |
| Vazamento em evidencias | Redacao de secrets e retencao proporcional ao risco. |

## Melhoria possivel

Enviar eventos para uma trilha de auditoria com retencao definida e criar alerta para bloqueios repetidos ou tentativas de bypass.

Fonte oficial: [Governance, Guardrails, and Operations](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/).
