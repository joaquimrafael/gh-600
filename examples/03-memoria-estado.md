# Exemplo do Dominio 3 - Memoria e estado com fonte de verdade

## Problema

Um agente retoma uma tarefa em outra sessao. Ele precisa distinguir conhecimento duravel, estado atual e anotacoes temporarias para nao agir com contexto obsoleto.

## Snapshot de exemplo

```yaml
task: issue-42
source_of_truth:
  requirements: issue-42
  implementation: pull-request-108
  validation: workflow-run-9002
durable_memory:
  - repository convention: validation errors use status 422
current_state:
  branch: fix/42-email-obrigatorio
  head_sha: abc1234
  completed:
    - input validation
  pending:
    - regression test
session_only:
  - inspect tests/auth next
freshness:
  captured_at: "2026-09-22T10:00:00-03:00"
  base_sha: def5678
```

O YAML representa um handoff de estudo. Antes de usá-lo, o agente deve conferir as fontes indicadas no GitHub.

## Regras de uso

| Informacao | Tipo | Acao ao retomar |
| --- | --- | --- |
| Convencao de status `422` | Memoria duravel | Confirmar na documentacao ou no codigo atual. |
| Branch, SHA e item pendente | Estado persistente | Comparar com a PR e o workflow mais recentes. |
| Proximo arquivo a inspecionar | Contexto da sessao | Descartar se a estrategia mudou. |
| Resultado do workflow | Estado externo | Usar apenas se pertence ao `head_sha` atual. |

## Como executar o exercicio

1. Considere que a PR agora aponta para o SHA `xyz9999`, e nao `abc1234`.
2. Classifique cada campo do snapshot como `reutilizar`, `revalidar` ou `descartar`.
3. Reancore o estado consultando issue, PR, commit atual e check mais recente, nessa ordem.
4. Produza um novo snapshot com o SHA atual e somente o trabalho ainda pendente.

## Resultado esperado

- Os requisitos da issue sao reutilizados depois de confirmar que nao mudaram.
- O estado de implementacao e o resultado do workflow sao revalidados porque o SHA mudou.
- A anotacao `inspect tests/auth next` pode ser descartada se a nova PR ja tiver esse teste.
- Nenhum resultado associado ao commit antigo e usado como evidencia do commit atual.

## O que observar

Memoria ajuda a localizar a informacao, mas nao substitui a fonte de verdade. Mudanca de SHA, requisitos ou branch base e um sinal para revalidar o contexto e evitar context drift.

## Melhoria possivel

Definir um schema para o handoff com campos obrigatorios de origem, timestamp, commit e regra de expiracao.

Fonte oficial: [Memory, State, and Evaluation](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/).
