# Exemplo do Dominio 5 - Orquestracao por artefatos

## Problema

Agentes de pesquisa, implementacao e revisao precisam colaborar sem compartilhar uma memoria invisivel nem alterar a mesma branch ao mesmo tempo.

## Papeis

| Agente | Entrada | Responsabilidade | Saida | Pode escrever codigo? |
| --- | --- | --- | --- | --- |
| Pesquisador | Issue e repositorio | Localizar componentes, restricoes e riscos. | `research-report.md` | Nao |
| Implementador | Issue e relatorio aprovado | Alterar caminhos permitidos e executar testes. | Branch, commits e `implementation-report.md` | Sim, na branch da tarefa |
| Revisor | Diff, criterios e relatorios | Comparar resultado, riscos e evidencias. | Check `approve`, `request-changes` ou `escalate` | Nao |

## Fluxo

```text
Issue
  -> Pesquisador
  -> research-report.md
  -> aprovacao do escopo
  -> Implementador
  -> branch + commits + implementation-report.md
  -> Revisor
  -> check e handoff humano
```

Formato minimo do handoff:

```yaml
task: issue-42
from: implementer
to: reviewer
head_sha: abc1234
changed_paths:
  - src/validation.ts
  - tests/validation.test.ts
checks:
  unit-tests: success
open_risks:
  - production metrics not yet observed
decision_needed: approve-or-request-changes
```

## Como executar o exercicio

1. Use a issue ficticia do [exemplo do Dominio 1](01-fluxo-agente-sdlc.md).
2. Produza um relatorio de pesquisa com arquivos provaveis, restricoes e perguntas abertas.
3. Considere o relatorio aprovado e produza o handoff do implementador no formato acima.
4. Simule o revisor encontrando um terceiro arquivo alterado fora do escopo.
5. Registre `request-changes`, identifique o caminho conflitante e encaminhe a decisao a uma pessoa.

## Regras de coordenacao

- Etapas dependentes sao sequenciais; analises independentes podem ocorrer em paralelo.
- Cada agente recebe somente as ferramentas e caminhos necessarios ao seu papel.
- Cada tarefa e agente usa branch ou saida isolada.
- Um handoff sem SHA, evidencias ou riscos permanece incompleto.
- Depois de duas falhas equivalentes, o fluxo para e escala em vez de repetir indefinidamente.
- A palavra final sobre merge pertence ao responsavel humano e as politicas do repositorio.

## O que observar

O artefato torna a passagem de responsabilidade revisavel e atribuivel. O revisor nao precisa confiar em uma conversa privada: ele consegue comparar issue, SHA, diff, checks e riscos registrados.

## Melhoria possivel

Validar automaticamente o schema do handoff e usar controles de concorrencia para impedir duas execucoes do implementador na mesma tarefa.

Fonte oficial: [Multi-Agent Systems and Orchestration](https://learn.microsoft.com/en-us/training/modules/multi-agent-systems-orchestration/).
