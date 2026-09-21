# Roteiro GH-600

Este roteiro separa a sequencia didatica do curso da cobertura exigida pela prova.

## Fontes oficiais

- [Curso GH-600T00-A - Developing in Agentic AI Systems](https://learn.microsoft.com/en-us/training/courses/gh-600t00)
- [Trilha 1 de 2](https://learn.microsoft.com/en-us/training/paths/gh-developing-agentic-systems-1/)
- [Trilha 2 de 2](https://learn.microsoft.com/en-us/training/paths/github-agentic-systems-part-two/github-agentic-systems-part-two)
- [Guia de estudo da prova GH-600](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/gh-600)
- [GitHub Docs](https://docs.github.com/en)

## Duas estruturas diferentes

### Modulos do curso

O curso GH-600T00-A e organizado em duas trilhas de aprendizagem, cada uma com tres modulos. Essa e a ordem usada para leitura e para os resumos em `docs/`.

### Dominios da prova

A prova GH-600 mede seis dominios com pesos proprios. Essa e a estrutura usada para verificar cobertura e organizar os checkpoints em `exercises/`.

Um modulo do curso nao equivale necessariamente a um dominio da prova. Por exemplo, memoria e avaliacao aparecem juntas no quinto modulo do curso, mas sao dois dominios separados na prova. A ordem tambem muda: multiagente e o quarto modulo do curso e o quinto dominio da prova.

## Modulos do curso

### Trilha 1 de 2

#### 1. Fundamentos da IA agente no GitHub

- [x] Estudar o ciclo planejar, agir e avaliar.
- [x] Entender o GitHub como sistema de registro e plano de controle.
- [x] Identificar responsabilidades, riscos, antipadroes e necessidades de rastreabilidade.
- Resumo: [Fundamentos da IA agente no GitHub](01-fundamentos-ia-agente.md)
- Modulo oficial: [Foundations of Agentic AI in GitHub](https://learn.microsoft.com/en-us/training/modules/foundations-agentic-ai/)

#### 2. Arquitetura do agente e integracao com o SDLC

- [ ] Mapear responsabilidades e boundaries do agente no SDLC.
- [ ] Definir entradas, saidas e criterios de sucesso.
- [ ] Separar planejamento, raciocinio e execucao.
- [ ] Revisar governanca por PR, checks, CODEOWNERS, regras e environments.
- Resumo: [Arquitetura do agente e integracao com o SDLC](02-arquitetura-agente-integracao.md)
- Modulo oficial: [Designing Agent Architecture and SDLC Integration](https://learn.microsoft.com/en-us/training/modules/design-agent-architecture-integration/)
- Status: em andamento.

#### 3. Ferramentas, MCP e ambientes de execucao

- [ ] Entender como agentes interagem com APIs e workflows do GitHub.
- [ ] Configurar MCP servers, registries e allow lists.
- [ ] Definir contexto, boundaries, limites e protecoes de execucao.
- Resumo: [Ferramentas, MCP e ambientes de execucao](03-ferramentas-mcp-ambientes.md)
- Modulo oficial: [Tooling, MCP, and Agent Execution Environments](https://learn.microsoft.com/en-us/training/modules/agent-tooling-mcp-execution-environments/)

### Trilha 2 de 2

#### 4. Sistemas multiagente e orquestracao

- [ ] Definir responsabilidades e coordenar agentes com GitHub workflows.
- [ ] Isolar execucoes e tratar conflitos, falhas e recuperacao.
- [ ] Produzir evidencias, atribuicao e handoffs observaveis.
- Resumo: [Sistemas multiagente e orquestracao](04-sistemas-multiagente-orquestracao.md)
- Modulo oficial: [Multi-Agent Systems and Orchestration](https://learn.microsoft.com/en-us/training/modules/multi-agent-systems-orchestration/)

#### 5. Memoria, estado e avaliacao

- [ ] Escolher estrategias de memoria e persistir estado.
- [ ] Controlar context drift e continuidade entre ferramentas e ambientes.
- [ ] Definir sinais de avaliacao, quality gates e analise de falhas.
- Resumo: [Memoria, estado e avaliacao](05-memoria-estado-avaliacao.md)
- Modulo oficial: [Memory, State, and Evaluation](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/)

#### 6. Governanca, guardrails e operacoes

- [ ] Definir autonomia e boundaries baseados em risco.
- [ ] Aplicar controles do GitHub, aprovacoes humanas e menor privilegio.
- [ ] Garantir observabilidade, auditoria e confiabilidade operacional.
- Resumo: [Governanca, guardrails e operacoes](06-governanca-guardrails-operacoes.md)
- Modulo oficial: [Governance, Guardrails, and Operations](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/)

### Modulo complementar

#### Casos de uso de IA para desenvolvedores com GitHub Copilot

Este modulo pertence a trilha **GitHub Copilot Fundamentals Part 1 of 2** e nao aos seis modulos oficiais do curso GH-600T00-A. Ele foi incluido como complemento ao dominio 1 da prova por relacionar o GitHub Copilot ao fluxo do desenvolvedor e as etapas do SDLC.

- [ ] Identificar como o GitHub Copilot pode aumentar a produtividade do desenvolvedor.
- [ ] Relacionar casos de uso do Copilot as etapas do SDLC.
- [ ] Entender como preferencias individuais afetam a experiencia de desenvolvimento.
- [ ] Avaliar limitacoes da codificacao assistida por IA e formas de medir seu impacto.
- Duracao oficial: 49 minutos, distribuidos em 7 unidades.
- Modulo oficial: [Developer use cases for AI with GitHub Copilot](https://learn.microsoft.com/en-us/training/modules/developer-use-cases-for-ai-with-github-copilot/)
- Cobertura complementar: dominio 1, com apoio aos dominios 2 e 4.
- Planejado para: 2026-09-21.

## Dominios da prova

1. **Preparar a arquitetura do agente e os processos do SDLC (15-20%)**
2. **Implementar o uso de ferramentas e a interacao com o ambiente (20-25%)**
3. **Gerenciar memoria, estado e execucao (10-15%)**
4. **Executar avaliacao, analise de erro e ajuste (15-20%)**
5. **Orquestrar a coordenacao multiagente (15-20%)**
6. **Implementar guardrails e prestacao de contas (10-15%)**

Os objetivos detalhados e os pesos devem ser conferidos no [guia oficial da prova](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/gh-600), que pode ser atualizado independentemente do curso.

## Mapa entre curso e prova

| Modulo do curso | Dominios da prova relacionados | Checkpoints praticos |
| --- | --- | --- |
| 1. Fundamentos | Base transversal, principalmente dominio 1 | [Dominio 1](../exercises/01-arquitetura-sdlc.md) |
| 2. Arquitetura e SDLC | Dominio 1; apoio aos dominios 2 e 6 | [Dominio 1](../exercises/01-arquitetura-sdlc.md) |
| 3. Ferramentas, MCP e ambientes | Dominio 2; apoio ao dominio 6 | [Dominio 2](../exercises/02-ferramentas-ambiente.md) |
| 4. Multiagente e orquestracao | Dominio 5 | [Dominio 5](../exercises/05-multiagente.md) |
| 5. Memoria, estado e avaliacao | Dominios 3 e 4 | [Dominio 3](../exercises/03-memoria-estado.md) e [Dominio 4](../exercises/04-avaliacao-ajuste.md) |
| 6. Governanca, guardrails e operacoes | Dominio 6; aplicacao transversal | [Dominio 6](../exercises/06-guardrails.md) |
| Complementar: casos de uso do Copilot | Dominio 1; apoio aos dominios 2 e 4 | [Dominio 1](../exercises/01-arquitetura-sdlc.md) |

O mapa e uma organizacao de estudo baseada nos objetivos oficiais, nao uma declaracao de equivalencia exclusiva. Assuntos como observabilidade, permissoes e recuperacao aparecem em mais de um modulo e dominio.

## Como estudar

Para cada modulo do curso:

1. Leia a referencia oficial.
2. Registre conceitos e duvidas no resumo em `docs/`.
3. Consulte o mapa e avance os checkpoints dos dominios relacionados em `exercises/`.
4. Registre evidencias, erros e ajustes reproduziveis em `examples/`.
5. Atualize [o estado da sessao](session-status.md), mantendo separados o progresso do curso e a cobertura da prova.

## Conclusao

- [ ] Concluir e revisar os seis resumos dos modulos do curso.
- [ ] Concluir os seis checkpoints dos dominios da prova.
- [ ] Construir um pequeno agente ou uma especificacao de agente.
- [ ] Documentar arquitetura, ferramentas, avaliacao e controles.
- [ ] Registrar o que ainda precisa ser praticado.
