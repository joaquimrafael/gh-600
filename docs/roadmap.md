# Roteiro GH-600

Curso de referencia: [GH-600T00-A - Desenvolvimento em sistemas de IA agêntica](https://learn.microsoft.com/pt-br/training/courses/gh-600t00)

O curso cobre o uso de agentes dentro do SDLC, incluindo arquitetura, ferramentas, memoria, avaliacao, governanca e coordenacao.

## Como estudar

Para cada modulo:

1. Leia a referencia principal.
2. Registre conceitos e duvidas em uma nota em `docs/`.
3. Resolva o checkpoint em `exercises/`.
4. Registre evidencias, erros encontrados e ajustes em `examples/`.

## Modulos

### 1. Arquitetura do agente e SDLC

- [ ] Estudar os limites, responsabilidades e pontos de integracao do agente.
- [ ] Relacionar o agente ao planejamento, implementacao, revisao e operacao.
- Resumo: [Fundamentos da IA agente no GitHub](01-fundamentos-ia-agente.md)
- Modulo oficial: [Fundamentos da IA Agente no GitHub](https://learn.microsoft.com/pt-br/training/modules/foundations-agentic-ai/)
- Leitura: [Preparar a arquitetura do agente e os processos do SDLC](https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-organization/prepare-for-custom-agents)
- Exercicio: [01-arquitetura-sdlc.md](../exercises/01-arquitetura-sdlc.md)

### 2. Ferramentas e interacao com o ambiente

- [ ] Definir quais ferramentas o agente pode usar.
- [ ] Entender ambientes, permissoes e interacao com o workspace.
- Leitura: [Implementar o uso da ferramenta e a interacao com o ambiente](https://docs.github.com/copilot/how-tos/copilot-sdk/use-copilot-sdk/custom-agents)
- Exercicio: [02-ferramentas-ambiente.md](../exercises/02-ferramentas-ambiente.md)

### 3. Memoria, estado e execucao

- [ ] Diferenciar memoria de repositorio, preferencias e estado de uma sessao.
- [ ] Observar como contexto e execucao influenciam o resultado.
- Leitura: [Gerenciar memoria, estado e execucao](https://docs.github.com/copilot/concepts/agents/copilot-memory)
- Exercicio: [03-memoria-estado.md](../exercises/03-memoria-estado.md)

### 4. Avaliacao, analise de erro e ajuste

- [ ] Definir criterios de sucesso e casos de teste.
- [ ] Registrar falhas, causas provaveis e mudancas de prompt ou ferramentas.
- Leitura: [Executar avaliacao, analise de erro e ajuste](https://docs.github.com/copilot/tutorials/customization-library/custom-agents/implementation-planner)
- Exercicio: [04-avaliacao-ajuste.md](../exercises/04-avaliacao-ajuste.md)

### 5. Coordenacao de varios agentes

- [ ] Separar papeis entre agentes pesquisadores, implementadores e revisores.
- [ ] Definir delegacao, escopo de ferramentas e tratamento de falhas.
- Leitura: [Orquestrar a coordenacao de varios agentes](https://docs.github.com/copilot/how-tos/copilot-sdk/use-copilot-sdk/custom-agents)
- Exercicio: [05-multiagente.md](../exercises/05-multiagente.md)

### 6. Guardrails e prestacao de contas

- [ ] Definir permissoes, limites, aprovacao humana e registro de evidencias.
- [ ] Avaliar riscos, mitigacoes e comportamento em caso de falha.
- Leituras: [Implementar guardrails](https://docs.github.com/copilot/tutorials/cloud-agent/build-guardrails) e [Riscos e mitigacoes](https://docs.github.com/en/copilot/concepts/agents/cloud-agent/risks-and-mitigations)
- Exercicio: [06-guardrails.md](../exercises/06-guardrails.md)

## Conclusao

- [ ] Revisar as notas dos seis modulos.
- [ ] Construir um pequeno agente ou especificacao de agente.
- [ ] Documentar arquitetura, ferramentas, avaliacao e controles.
- [ ] Registrar o que ainda precisa ser praticado.
