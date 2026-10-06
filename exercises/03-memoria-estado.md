# Dominio 3 - Memoria, estado e execucao

Peso na prova: **10-15%**.

Modulo principal do curso: [Memory, State, and Evaluation](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/).

## Tarefa

Documente o que um agente deve lembrar entre tarefas e o que deve existir apenas durante uma sessao.

## Entregavel

- Tabela com memoria, estado temporario e fonte de cada dado.
- Exemplo de informacao obsoleta.
- Regra para validar ou descartar contexto antigo.

## Reflexao

- Como a memoria pode melhorar o trabalho?
- Que risco existe ao guardar informacao incorreta?

## Resposta

Entre as tarefas, o agente deve lembrar:

A fonte de verdade sobre o contexto do repositorio, as mudancas planejadas e o plano atualizado deve estar armazenada na memoria externa, em documentacao, codigo, issues e PRs.

Deve lembrar na memoria duravel as principais decisoes tomadas, os padroes e convencoes, e coisas a serem reutilizadas. Esse conhecimento pode estar registrado na memoria externa; duracao e local de armazenamento nao sao a mesma coisa.

Ja na memoria de curto prazo, guardar o contexto de trabalho da sessao, como a proxima busca ou uma hipotese ainda nao confirmada. As tarefas feitas e a serem feitas, as decisoes e os resultados dos commits devem ficar registrados como estado duravel, para nao se perderem ao trocar de sessao.

| Informacao | Tipo | Fonte do dado | Como usar ao retomar |
| --- | --- | --- | --- |
| Requisitos e criterios de aceite | Memoria externa duravel | Issue vinculada a PR | Conferir se os requisitos mudaram. |
| Plano atualizado e decisoes | Memoria externa e estado duravel | Descricao e discussoes da PR | Retomar a estrategia atual, nao uma copia antiga do plano. |
| Padroes e convencoes reutilizaveis | Memoria de longo prazo | Instrucoes e documentacao do repositorio | Confirmar que ainda se aplicam ao codigo atual. |
| Tarefas feitas e pendentes, branch e SHA | Estado duravel | PR e historico de commits | Conferir o progresso antes de repetir trabalho. |
| Resultado de testes e checks | Estado externo | Workflow run associado ao SHA avaliado | Nao usar o resultado de um commit antigo como validacao do atual. |
| Proxima busca e hipotese de investigacao | Contexto temporario da sessao | Contexto de trabalho do agente | Descartar se o objetivo ou a estrategia mudou; persistir apenas conclusoes relevantes. |

Informacao obsoleta: nome de variavel que foi trocado, tarefa de teste ja concluida ou check aprovado para um commit que foi substituido.

Regra para validar ou descartar: comparar o contexto antigo com a issue, a PR, o SHA atual e os workflows mais recentes. Se os requisitos, o codigo ou a estrategia mudaram, atualizar ou descartar a informacao substituida. Em caso de contradicao entre fontes, esclarecer qual e a decisao atual antes de continuar, sem escolher uma versao por conta propria.

A memoria pode melhorar o trabalho mantendo uma fonte de verdade clara para cada tipo de informacao, descartando informacoes irrelevantes e permitindo acesso mais rapido a pontos criticos, sem repetir trabalho.

O risco e de gerar erros de codigo na passagem de contexto ao agente, conflitos e contradicoes nos artefatos do GitHub, alem de tomar decisoes com base em requisitos ou resultados obsoletos.

Fontes oficiais: [estrategias de memoria](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/2-agent-memory-strategies) e [continuidade entre ferramentas e ambientes](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/4-memory-state-continuity).
