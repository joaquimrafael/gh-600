# Dominio 5 - Coordenacao multiagente

Peso na prova: **15-20%**.

Modulo principal do curso: [Multi-Agent Systems and Orchestration](https://learn.microsoft.com/en-us/training/modules/multi-agent-systems-orchestration/).

## Tarefa

Modele uma equipe com agentes de pesquisa, implementacao e revisao.

## Entregavel

- Papeis e responsabilidades.
- Regra de delegacao.
- Dados trocados entre agentes.
- Comportamento quando um agente falha.

## Reflexao

- Que tarefas podem ocorrer em paralelo?
- Quem tem a palavra final?

## Resposta

### Agente de pesquisa

- Papeis e responsabilidades: Entender o contexto do repositorio como um todo, levantar requisitos sobre uma demanda e propor relatorios e planos estruturados sobre mudancas no codigo, a serem implementados.
- Regra de delegacao: Entregar um plano estruturado em arquivo .md ao agente implementador depois da validacao do escopo e dos criterios de aceite pelo responsavel humano.
- Dados trocados: objetivo da demanda, requisitos, criterios de aceite, caminhos permitidos, fontes consultadas e riscos identificados.
- Em caso de falha: Fazer no maximo duas novas tentativas para falhas transitorias e escalar se persistirem. Falhas de permissao ou seguranca devem ser escaladas imediatamente.
- Permissoes: leitura apenas, e acesso as issues do repo.

### Agente de implementacao

- Papeis e responsabilidades: A partir de um artefato (documento) estruturado, implementar as mudancas em codigo nos caminhos permitidos seguindo as diretrizes do projeto, e fornecer um relatorio sobre o que foi feito e os resultados obtidos.
- Regra de delegacao: Atuar em branch isolada e encaminhar o PR e o relatorio de implementacao ao agente revisor quando as mudancas e as evidencias de validacao estiverem prontas.
- Dados trocados: plano original, link do PR, SHA do commit revisado, caminhos alterados, decisoes, resultados dos testes e riscos pendentes.
- Em caso de falha: Fazer no maximo duas tentativas de correcao dentro do escopo e escalar se o problema persistir. Falhas de permissao ou seguranca devem ser escaladas imediatamente.
- Permissoes: escrita em caminhos permitidos, execucao de testes e mudancas apenas em branches nao protegidas.

### Agente de revisao

- Papeis e responsabilidades: Revisar o PR do agente implementador e seu respectivo relatorio, revisitando o plano original e atentando-se a detalhes importantes para avaliar a seguranca e a qualidade do codigo, executando as checagens e produzindo um relatorio de analise das mudancas para apoiar a aprovacao humana do PR.
- Regra de delegacao: Devolver ao implementador os pontos que precisam de correcao ou encaminhar seu parecer e as evidencias ao responsavel humano para aprovacao.
- Dados trocados: SHA revisado, achados, resultados das verificacoes, riscos pendentes e recomendacao de aprovacao ou correcao.
- Em caso de falha: Escalar imediatamente quando nao conseguir concluir a revisao. Pedir correcoes no codigo e feedback ao implementador, nao uma falha do agente revisor.
- Permissoes: apenas leitura e execucao das verificacoes.

As etapas de pesquisa, implementacao e revisao da mesma tarefa ocorrem em sequencia, visto que possuem dependencias entre si. Pesquisas independentes ou verificacoes de seguranca e testes podem ocorrer em paralelo quando nao dependem umas das outras nem disputam o mesmo estado.

Quem tem a palavra final e o responsavel humano pela aprovacao, respeitando os checks e as politicas do repositorio. O agente revisor recomenda aprovacao ou correcoes com base nas evidencias, mas seu parecer sozinho nao garante que o resultado seja seguro de entrar nos ambientes.
