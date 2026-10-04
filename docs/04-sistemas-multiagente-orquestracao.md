# Curso - Modulo 4: Sistemas multiagente e orquestracao

Fonte: [Multi-Agent Systems and Orchestration](https://learn.microsoft.com/en-us/training/modules/multi-agent-systems-orchestration/)

Cobertura da prova: principalmente o **Dominio 5 - Orquestrar a coordenacao multiagente**.

Este modulo apresenta uma abordagem baseada em GitHub para coordenar varios agentes. A confiabilidade vem de responsabilidades estreitas, execucoes isoladas, comunicacao por artefatos revisaveis e mecanismos explicitos para detectar conflitos, diagnosticar falhas e recuperar o fluxo.

## Resumo

### 1. Responsabilidades e boundaries claros

Cada agente deve ter um papel pequeno, verificavel e associado a artefatos do GitHub. Sem essa divisao, agentes duplicam trabalho, alteram os mesmos arquivos e deixam a responsabilidade pelo resultado ambigua.

Um modelo seguro mantem a fronteira: agentes propoem; pessoas e politicas aceitam. Exemplos de responsabilidades:

- agente de dependencias altera manifests e lockfiles;
- agente de refatoracao trabalha em caminhos de codigo definidos;
- agente de seguranca valida resultados e produz relatorios;
- workflows e checks produzem evidencias;
- CODEOWNERS e revisores decidem a aceitacao.

O escopo pode ser limitado por caminhos, tipos de artefato, permissoes e sinais de conclusao.

### 2. Orquestracao por eventos e artefatos

Orquestrar significa definir quando cada agente executa, como as tarefas sao encadeadas e como os resultados passam de uma etapa para outra.

No GitHub, essa coordenacao deve aparecer em eventos, workflow runs, checks e artefatos:

- execucao sequencial quando uma saida depende da etapa anterior;
- execucao paralela quando os escopos nao se sobrepoem;
- fan-out/fan-in quando analises independentes executam em paralelo e uma etapa posterior combina os resultados;
- gatilhos por agenda, pull request ou conclusao de outro workflow.

Artefatos estruturados, como planos e relatorios, sao preferiveis a comunicacao invisivel entre agentes. Eles separam raciocinio de escrita, permitem revisao e deixam um historico duravel.

### 3. Isolamento para execucao paralela

Paralelismo confiavel exige isolamento:

- branch dedicada por agente e tarefa;
- workflow ou job com responsabilidade clara;
- menor privilegio por workflow ou job;
- controles de concorrencia por workflow e branch;
- saidas separadas e atribuiveis.

O grupo de concorrencia deve ser especifico o bastante para cancelar execucoes antigas da mesma atividade sem bloquear workflows independentes. Compartilhar branch, permissoes amplas ou contexto de execucao dificulta atribuicao, rollback e diagnostico.

### 4. Conflitos e arbitragem

Mesmo com isolamento, conflitos podem ocorrer:

- conflito textual: agentes alteram as mesmas linhas;
- conflito semantico: o merge e limpo, mas o comportamento combinado quebra;
- conflito de politica: caminhos exigem revisoes diferentes;
- esforco duplicado: duas PRs resolvem o mesmo problema de formas incompatíveis.

O GitHub fornece mecanismos de arbitragem como validacao de merge, required checks, CODEOWNERS e revisao de PR. Regras de escalacao devem interromper tentativas repetidas e informar o que conflitou, o que foi tentado e quais opcoes restam. O resultado nao deve ser decidido apenas pela PR que chegou primeiro.

### 5. Observabilidade, atribuicao e handoffs

Cada etapa relevante precisa deixar evidencias duraveis:

- pull request com objetivo e plano;
- labels ou nomes que identifiquem o agente;
- checks, workflow runs e logs;
- artefatos com resultados estruturados;
- decisoes, riscos e proximo responsavel registrados no handoff.

Observabilidade permite responder quem agiu, o que foi feito, por que uma decisao foi tomada e qual evidencia sustenta o resultado. Sem isso, o sistema nao pode ser depurado ou auditado de forma confiavel.

### 6. Falhas e recuperacao segura

Falhas multiagente frequentemente sao falhas de coordenacao:

- execucao parcial;
- workflow parado;
- saidas conflitantes;
- execucoes repetidas que nao convergem;
- aprovacao ou handoff ausente.

O diagnostico usa a timeline da PR, resultados de checks, historico de workflows, logs e artefatos. A recuperacao combina retries limitados, rollback, PRs pequenos e escalacao humana. Se o mesmo erro persistir, a automacao deve parar em vez de entrar em loop.

Projetar para falha significa assumir que agentes e workflows podem nao convergir e definir antecipadamente como detectar, limitar e reverter o impacto.

## Checklist de aprendizado

- [x] Consigo atribuir responsabilidades estreitas e nao sobrepostas a varios agentes.
- [x] Sei escolher entre orquestracao sequencial, paralela e fan-out/fan-in.
- [x] Entendo como branches, workflows, permissoes e concorrencia isolam execucoes.
- [x] Sei diferenciar conflitos textuais, semanticos, de politica e de duplicidade.
- [x] Consigo definir evidencias e handoffs revisaveis no GitHub.
- [ ] Sei propor retry limitado, rollback e escalacao para falhas de coordenacao.

## Perguntas de revisao

1. Por que papeis genericos aumentam o risco em um sistema multiagente?
2. Quando agentes podem executar em paralelo?
3. Qual e a vantagem de coordenar agentes por artefatos?
4. Como CODEOWNERS participa da resolucao de conflitos?
5. Que sinais indicam que a automacao deve parar e escalar?

## Respostas

1. Isso ocorre pois, sem responsabilidades bem definidas, os agentes acabam se sobrepondo na realizacao de tarefas, gerando trabalho duplicado e conflitos no repositorio, alem de deixar ambigua a responsabilidade pelo resultado, o que compromete a qualidade da aplicacao.

2. Os agentes podem executar em paralelo quando nao possuem dependencias entre si, ou seja, um nao precisa do resultado, handoff ou acao do outro, e podem atuar de forma isolada, sem se sobrepor gerando duplicacoes e conflitos. Mesmo assim, os resultados precisam ser validados quando forem integrados.

3. A principal vantagem e que os artefatos tornam as passagens de responsabilidade revisaveis e atribuiveis, facilitando a revisao, o diagnostico de falhas e a rastreabilidade durante todo o ciclo de vida do software.

4. O CODEOWNERS participa da resolucao de conflitos identificando os individuos ou equipes responsaveis por partes especificas do codigo e solicitando sua revisao. Essas pessoas ajudam a decidir sobre as mudancas conflitantes, mas o arquivo nao resolve os conflitos automaticamente. A aprovacao dos responsaveis so e obrigatoria quando configurada nas regras do repositorio.

5. Os principais sinais sao: falhas nao transitorias sem recuperacao segura dentro do escopo, limite de retentativas atingido, execucoes repetidas sem convergencia e alertas criticos que exigem decisao humana. Conflitos em merge gerados por agentes e execucoes parciais precisam de diagnostico e devem ser escalados quando a recuperacao permitida nao resolve o problema.

## Relacao com o GH-600

Este modulo cobre coordenacao, isolamento, conflitos, observabilidade, recuperacao e handoffs entre agentes. Ele transforma varios agentes independentes em um sistema operavel e auditavel dentro do GitHub.
