# Curso - Modulo 5: Memoria, estado e avaliacao

Fonte: [Memory, State, and Evaluation](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/)

Cobertura da prova: **Dominio 3 - Gerenciar memoria, estado e execucao** e **Dominio 4 - Executar avaliacao, analise de erro e ajuste**.

Este modulo combina duas necessidades de um agente confiavel: manter continuidade sem acumular contexto incorreto e avaliar o resultado por sinais verificaveis. O GitHub funciona como fonte duravel de estado por meio de issues, pull requests, commits, checks, logs e artefatos.

## Resumo

### 1. Tipos de memoria

A memoria do agente pode ser organizada em tres categorias:

- **curto prazo**: contexto de trabalho da tarefa atual, como instrucoes recentes e proximas etapas;
- **longo prazo**: conhecimento selecionado e reutilizavel, como decisoes e padroes consolidados;
- **externa**: informacao persistida fora da sessao, como issues, PRs, documentacao, logs e artefatos.

A memoria externa atua como fonte de verdade porque persiste entre sessoes e pode ser revisada. Requisitos e criterios de aceite pertencem a issues ou PRs; decisoes devem ficar em artefatos duraveis; processos repetiveis devem virar instrucoes ou skills.

Memoria util e seletiva. Informacao duplicada, temporaria ou sem impacto no resultado aumenta confusao e favorece o uso de contexto obsoleto.

### 2. Estado persistente e pull request como ancora

Memoria indica o que importa; estado registra o que ja foi feito, quais decisoes foram tomadas e o que ainda falta.

No GitHub, o estado e distribuido entre:

- issue com objetivo e criterios de aceite;
- branch e commits com progresso incremental;
- pull request com plano, decisoes e discussoes;
- workflow runs, checks e artefatos com resultados de validacao.

A pull request funciona como ancora central porque agrega mudancas, commits, checks e feedback. Para retomar uma tarefa, o agente deve consultar a PR existente, o issue vinculado, os commits e os resultados mais recentes, evitando recomecar ou repetir trabalho.

### 3. Context drift, expiracao e reset

Context drift ocorre quando a execucao deixa de refletir o objetivo original ou decisoes anteriores. Ele pode ser detectado comparando:

- mudancas da PR com criterios de aceite;
- commits atuais com decisoes registradas;
- resultados dos checks com o estado esperado;
- branch de trabalho com a branch base atual.

A correcao exige voltar a fonte de verdade, atualizar os artefatos e executar novamente as validacoes.

Memoria tambem precisa de manutencao:

- expiracao para dados temporarios;
- pruning de artefatos antigos ou redundantes;
- sumarizacao de historicos extensos;
- reset quando requisitos, estrategia ou premissas mudam.

### 4. Continuidade entre ferramentas e ambientes

Um agente pode iniciar no IDE, continuar na CLI e finalizar em um ambiente hospedado. A continuidade nao deve depender do historico de uma sessao, mas de referencias duraveis como:

- numero da PR e nome da branch;
- SHA de commit;
- URL da issue ou PR;
- link para workflow run;
- artefatos produzidos pela execucao.

Cada tipo de informacao deve ter uma fonte de verdade. Copiar requisitos ou decisoes para varios prompts cria versoes conflitantes. Ao mudar de ambiente, o agente deve se reancorar no estado mais recente do GitHub e confirmar commits, checks e criterios atuais.

### 5. Sinais de avaliacao e quality gates

A avaliacao comeca antes da execucao, com criterios de sucesso claros. Eles devem descrever comportamento esperado, testes obrigatorios, restricoes operacionais e condicoes de seguranca.

Sinais de avaliacao podem incluir:

- testes, lint e build;
- required status checks;
- revisoes obrigatorias;
- code scanning e dependency review;
- secret scanning e push protection;
- logs, relatorios e artefatos.

Quality gates transformam esses sinais em regras de aceitacao. Branch protection, rulesets e checks obrigatorios impedem o merge quando as evidencias nao atendem ao criterio definido.

### 6. Analise de falhas e ajuste

Falhas devem ser analisadas comparando intencao e resultado. Issues e PRs registram o que deveria acontecer; commits, logs e artefatos mostram o que ocorreu.

As causas podem ser classificadas em:

- **erro de raciocinio**: requisito mal interpretado, premissa incorreta ou logica inadequada;
- **uso incorreto de ferramenta**: comando, workflow, permissao ou gatilho errado;
- **problema de contexto**: informacao ausente, desatualizada ou conflitante.

Depois da classificacao, o ajuste deve atingir a causa correspondente:

- melhorar prompts e instrucoes;
- corrigir memoria, estado ou fonte de verdade;
- alterar ferramentas, permissoes e workflows.

O ciclo e executar, observar evidencias, identificar a causa, ajustar e validar novamente. Todas as mudancas de comportamento precisam continuar rastreaveis.

## Checklist de aprendizado

- [ ] Consigo diferenciar memoria de curto prazo, longo prazo e externa.
- [ ] Sei registrar progresso e decisoes como estado duravel no GitHub.
- [ ] Consigo detectar context drift e reancorar o agente na fonte de verdade.
- [ ] Entendo regras de expiracao, pruning, sumarizacao e reset.
- [ ] Sei definir sinais de avaliacao e quality gates verificaveis.
- [ ] Consigo classificar falhas de raciocinio, ferramenta e contexto.
- [ ] Sei escolher um ajuste coerente com a causa identificada.

## Perguntas de revisao

1. Qual e a diferenca entre memoria e estado?
2. Por que a pull request pode funcionar como ancora de estado?
3. Como evitar contexto conflitante entre IDE, CLI e ambiente hospedado?
4. Qual e a diferenca entre um sinal de avaliacao e um quality gate?
5. Como a classificacao da causa melhora o ajuste do agente?

## Respostas

1.

2.

3.

4.

5.

## Relacao com o GH-600

Este modulo une dois dominios da prova. A primeira metade cobre memoria, estado, continuidade e drift; a segunda cobre criterios de sucesso, sinais, gates, analise de causa e ajuste iterativo.
