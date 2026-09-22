# Exemplo do Dominio 1 - Fluxo de um agente no SDLC

## Problema

Um agente deve corrigir um erro de validacao sem alterar diretamente a branch `main`. O fluxo precisa tornar plano, execucao, avaliacao e aprovacao humana visiveis no GitHub.

## Cenario

Issue ficticia `#42`:

```text
Objetivo: rejeitar cadastro sem endereco de e-mail.
Escopo: validacao de entrada e testes relacionados.
Fora do escopo: alterar banco de dados ou interface.
Criterios de aceite:
- entrada sem e-mail retorna erro de validacao;
- cadastros validos continuam funcionando;
- testes automatizados passam.
```

## Fluxo reproduzivel

| Etapa | Responsabilidade do agente | Evidencia no GitHub | Gate |
| --- | --- | --- | --- |
| Planejar | Ler a issue, localizar o codigo afetado e propor arquivos e testes. | Comentario com plano na issue `#42`. | Uma pessoa confirma escopo e criterios. |
| Agir | Criar `fix/42-email-obrigatorio`, alterar somente validacao e testes e produzir commits pequenos. | Branch e commits vinculados a `#42`. | Token sem permissao de push em `main`. |
| Avaliar | Executar testes e comparar o diff com os criterios de aceite. | Checks e relatorio de testes. | Falha em qualquer check bloqueia o merge. |
| Entregar | Abrir uma pull request com resumo, risco, evidencia e plano de rollback. | PR vinculada a `#42`. | Revisao obrigatoria e CODEOWNERS quando aplicavel. |
| Operar | Depois do merge, observar falhas de cadastro e reverter se houver regressao. | Deploy, logs e issue de incidente, se necessaria. | Aprovacao do environment para producao. |

## Como executar o exercicio

1. Leia a issue ficticia e escreva um plano de no maximo cinco passos.
2. Para cada passo, indique qual arquivo seria alterado e qual evidencia provaria sua conclusao.
3. Simule um check de testes com resultado `failure`.
4. Confirme que o fluxo para na etapa de avaliacao e nao chega ao merge.
5. Troque o resultado para `success`, registre uma aprovacao humana e conclua o fluxo.

## O que observar

- O agente propoe e valida, mas nao aprova a propria alteracao.
- A branch isola a escrita; a PR concentra plano, diff, checks e revisoes.
- O gate usa evidencia verificavel, nao apenas a afirmacao do agente de que terminou.
- Uma falha de teste impede a transicao para entrega.

## Riscos e controles

| Risco | Controle |
| --- | --- |
| Alteracao fora do escopo | Lista explicita de caminhos permitidos e revisao do diff. |
| Push direto na `main` | Ruleset ou protecao de branch e permissao minima do token. |
| Regressao aceita sem evidencia | Checks obrigatorios e revisao humana. |

## Melhoria possivel

Transformar os criterios de aceite em um template de issue e adicionar um check que verifique se a PR referencia a issue de origem.

Fonte oficial: [Designing Agent Architecture and SDLC Integration](https://learn.microsoft.com/en-us/training/modules/design-agent-architecture-integration/).
