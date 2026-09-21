# Curso - Modulo 2: Arquitetura do agente e integracao com o SDLC

Fonte: [Designing Agent Architecture and SDLC Integration](https://learn.microsoft.com/en-gb/training/modules/design-agent-architecture-integration/)

Cobertura da prova: principalmente o **Dominio 1 - Preparar a arquitetura do agente e os processos do SDLC**, com fundamentos usados tambem nos dominios de ferramentas e guardrails.

Este modulo mostra como a arquitetura de um agente precisa ser pensada em conjunto com o ciclo de vida do software. Em vez de tratar o agente como um chatbot isolado, o foco e definir responsabilidades claras, regras de governanca, entradas e saidas bem estruturadas e fluxos observaveis.

## Resumo

### 1. Mapear responsabilidades do agente no SDLC

O agente deve participar de etapas do ciclo de vida com limites bem definidos, como:

- compreender e decompor requisitos;
- planejar tarefas e sequencias de execucao;
- implementar alteracoes em codigo ou configuracao;
- validar resultados com testes e chequeos;
- preparar pull requests e evidencias de entrega;
- monitorar operacao e apoiar manutencao.

A ideia central e que o agente nao substitui a decisao humana, mas tira parte do trabalho repetitivo e de apoio, dentro de um processo com revisao e governanca.

### 2. Definir entradas, saidas e criterio de sucesso

Para que um agente funcione de forma confiavel, todo trabalho precisa ter:

- objetivo claro;
- contexto suficiente para entender o problema;
- inputs bem definidos;
- outputs esperados;
- criterio de sucesso verificavel.

Sem isso, o agente tende a agir com base em suposicoes, o que aumenta risco de erro, escopo desviado e baixa rastreabilidade.

### 3. Separar planejar, raciocinar e executar

O modulo enfatiza que a arquitetura do agente precisa separar responsabilidades:

- planejar: identificar passos, dependencias e restricoes;
- raciocinar: interpretar contexto e decidir como resolver;
- executar: usar ferramentas para editar arquivos, testar e validar.

Essa separacao cria fluxos mais observaveis e facilita a revisao humana. Em vez de aceitar a primeira resposta plausivel, a equipe pode inspecionar a estrategia, os passos e as evidencias.

### 4. Governanca por pull request

O GitHub atua como espaco de governanca e rastreio. A arquitetura segura do agente depende de controles como:

- templates de pull request;
- checks de CI e qualidade;
- CODEOWNERS;
- regras de branch protection;
- ambientes e gates de aprovacao;
- requisitos de revisao manual.

Esses mecanismos evitam que o agente altere codigo sem contexto, sem aprovacao ou sem validacao relevante.

### 5. Fluxos confiaveis: outputs, contextos, gatilhos e handoffs

Em sistemas mais complexos, o agente nao precisa fazer tudo sozinho. O processo deve ser estruturado em etapas conectadas:

- uma etapa produz artefatos ou contexto;
- outra etapa usa esse contexto como entrada;
- gatilhos definem quando o processo avanca;
- handoffs entre jobs ou etapas ajudam a manter o fluxo claro.

Isso reduz acoplamento, facilita depuracao e melhora a auditabilidade do trabalho.

### 6. Operacao e controle do agente

O modulo tambem trata de operacao segura do agente, incluindo:

- observabilidade de logs, metricas e artefatos;
- governanca de ferramentas e permissao;
- uso de MCP para integrar ferramentas e contexto externo;
- limites de secrets e acesso a recursos sensiveis;
- hooks e validacoes de seguranca;
- firewall e restricoes de rede;
- padroes de confiabilidade para evitar falhas em cadeias de execucao.

Em outras palavras, o agente precisa operar dentro de um ambiente com limites claros e evidencias de execucao.

## Checklist de aprendizado

- [ ] Consigo mapear responsabilidades do agente ao SDLC.
- [ ] Sei distinguir objetivo, contexto, entrada, saida e criterio de sucesso.
- [ ] Entendo a diferenca entre planejamento, raciocinio e execucao.
- [ ] Reconheco a importancia de PRs, checks e regras de branch para governanca.
- [ ] Sei descrever como fluxos confiaveis e observabilidade reduzem risco.
- [ ] Entendo por que permissoes, secrets e limites de ferramentas sao parte da arquitetura.

## Perguntas de revisao

1. Qual e a vantagem de separar planejamento, raciocinio e execucao em um agente?
2. Como os controles de PR e regras de repositorio ajudam a governanca do agente?
3. O que deve estar presente em um criterio de sucesso bem definido?
4. Qual e a funcao de outputs, contextos e handoffs em um fluxo de trabalho?
5. Como observabilidade e limites de acesso reduzem risco operacional?

## Respostas

1. A separacao melhora rastreabilidade, reduz erros por suposicao e facilita a revisao humana, pois cada etapa pode ser inspecionada e ajustada separadamente.

2. Eles definem quando uma alteracao pode ser aceita, exigem validacoes e estabelecem limites de permissao e revisao, reduzindo risco de mudancas sem supervisao.

3. Um criterio de sucesso deve incluir objetivo, condicoes de aceitacao, verificacoes necessarias, contexto relevante e evidencias que comprovem que a entrega resolveu o problema.

4. Outputs e contextos transformam uma etapa em insumo para a proxima, enquanto handoffs mantem o fluxo organizado entre jobs, tarefas e validacoes.

5. Observabilidade permite reconstruir o que aconteceu e identificar falhas; limites de acesso e secrets impedem uso indevido de recursos sensiveis e reduzem impacto de execucao indevida.

## Relacao com o GH-600

Este modulo conecta diretamente os fundamentos do modulo anterior com a arquitetura pratica de agentes no GitHub. Ele prepara o estudo de ferramentas, memoria, avaliacao, multiagente e guardrails, mostrando que a confiabilidade de um agente depende tanto da inteligencia do modelo quanto da estrutura do processo e dos controles do repositorio.
