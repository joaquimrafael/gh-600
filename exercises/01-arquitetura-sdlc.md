# Dominio 1 - Arquitetura e processos do SDLC

Peso na prova: **15-20%**.

Fonte conceitual: [Fundamentos da IA agente no GitHub](../docs/01-fundamentos-ia-agente.md)

Modulos do curso relacionados: [Fundamentos da IA agente](../docs/01-fundamentos-ia-agente.md) e [Arquitetura do agente e integracao com o SDLC](../docs/02-arquitetura-agente-integracao.md).

## Tarefa

Desenhe o fluxo de um agente participando do SDLC, do requisito ao deploy e operacao. Inclua explicitamente as etapas planejar, agir e avaliar.

## Entregavel

- Diagrama ou lista das etapas.
- Responsabilidade do agente em cada etapa.
- Ponto de revisao humana.
- Evidencias registradas no GitHub: issue, branch, pull request, checks e artefatos.
- Pelo menos tres riscos e o respectivo controle.

## Fluxo do SDLC com IA agêntica

![Diagrama do SDLC com IA agêntica](SLDC..png)

## Reflexao

- Onde o agente pode causar impacto?

O agente pode causar impacto positivo em tarefas repetitivas, e que podem ser realizadas a partir de criterios bem definidos, permissoes minimas e acesso restrito, gerando velocidade, mas tambem pode causar impacto negativo se nao houver controle bem definido no github, executando acoes destrutivas e ou de alto impacto produtivo.

- Que informacao ele precisa em cada etapa?

1- Requisitos funcionais e nao funcionais, necessidade de negocio e objetivo do cliente


2- Permissoes, acessos, definicoes de codigo, padroes e historico do repositorio


3- Ferramentas, recursos, modelos, o plano e criterios de aceite


4- Testes, artefatos da esteira, comentarios e feedback


5- Aprovacao, fluxo de deploy, planejamento, plano de roolback


6- Logs, metricas, traces, impacto no cliente e dados de comprovacao
