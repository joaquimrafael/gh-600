# Estado da trilha

Atualizado em: 2026-09-22

## Convencao

O progresso e registrado em duas dimensoes:

- **modulos do curso**: definem a ordem de leitura dos resumos;
- **dominios da prova**: definem a cobertura e os exercicios praticos.

Consulte o [mapa entre curso e prova](roadmap.md#mapa-entre-curso-e-prova). As duas sequencias nao sao equivalentes.

## Progresso do curso

### Concluido

#### Curso - Modulo 1: Fundamentos da IA agente no GitHub

- Resumo: [docs/01-fundamentos-ia-agente.md](01-fundamentos-ia-agente.md)
- Diagrama: [exercises/SLDC..png](../exercises/SLDC..png)
- Evidencia pratica: [exercises/01-arquitetura-sdlc.md](../exercises/01-arquitetura-sdlc.md)
- Fonte: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/foundations-agentic-ai/)
- Status: concluido com resumo, diagrama do SDLC e reflexoes.

#### Curso - Modulo 2: Arquitetura do agente e integracao com o SDLC

- Resumo: [docs/02-arquitetura-agente-integracao.md](02-arquitetura-agente-integracao.md)
- Fonte: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/design-agent-architecture-integration/)
- Foco: responsabilidades, boundaries, entradas, saidas, criterios de sucesso, governanca por PR e fluxos confiaveis.
- Status: concluido em 2026-09-20, com resumo revisado, checklist validado e perguntas respondidas.

### Primeira revisao do Dominio 1 concluida

Dominio 1 - Preparar a arquitetura do agente e os processos do SDLC

- Cobertura conjunta dos modulos 1 e 2 revisada.
- [Exercicio do dominio 1](../exercises/01-arquitetura-sdlc.md) retomado e conceitos principais conferidos.
- Primeira revisao concluida em 2026-09-22, com [exemplo pratico](../examples/01-fluxo-agente-sdlc.md).

### Duvidas resolvidas durante a revisao

- Registrada a diferenca entre `CODEOWNERS`, rulesets e protecao de branch no [resumo do modulo 2](02-arquitetura-agente-integracao.md#dúvida-resolvida-qual-é-a-diferença-entre-codeowners-rulesets-e-proteção-de-branch).
- Aprendizado principal: `CODEOWNERS` define quem deve revisar; rulesets e protecao de branch definem as condicoes impostas pela plataforma.

### Atividade complementar concluida

Casos de uso de IA para desenvolvedores com GitHub Copilot

- Modulo: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/developer-use-cases-for-ai-with-github-copilot/)
- Duracao: 49 minutos, em 7 unidades.
- Relacao principal: complemento ao dominio 1 da prova e ao estudo do SDLC iniciado nos modulos 1 e 2 do curso.
- Foco: produtividade, preferencias do desenvolvedor, uso de IA nas etapas do SDLC, limitacoes e medicao de impacto.
- Status: concluido em 2026-09-22.

### Proximo modulo do curso

Curso - Modulo 3: Ferramentas, MCP e ambientes de execucao

- Inicio planejado para 2026-09-23, depois da conclusao da primeira revisao do dominio 1 e do modulo complementar.
- Resumo preparado: [docs/03-ferramentas-mcp-ambientes.md](03-ferramentas-mcp-ambientes.md).
- Checkpoint principal: [exercises/02-ferramentas-ambiente.md](../exercises/02-ferramentas-ambiente.md), referente ao dominio 2 da prova.

### Material preparado para os modulos seguintes

Os resumos abaixo ja foram criados a partir dos modulos oficiais, mas isso nao representa conclusao do estudo ou dos checklists:

- [Curso - Modulo 4: Sistemas multiagente e orquestracao](04-sistemas-multiagente-orquestracao.md)
- [Curso - Modulo 5: Memoria, estado e avaliacao](05-memoria-estado-avaliacao.md)
- [Curso - Modulo 6: Governanca, guardrails e operacoes](06-governanca-guardrails-operacoes.md)

## Cobertura da prova

| Dominio | Peso | Estado |
| --- | --- | --- |
| 1. Arquitetura e processos do SDLC | 15-20% | Primeira revisao concluida; modulos 1 e 2 concluidos e [exemplo preparado](../examples/01-fluxo-agente-sdlc.md) |
| 2. Ferramentas e ambiente | 20-25% | [Exemplo preparado](../examples/02-politica-ferramentas.md); exercicio nao concluido |
| 3. Memoria, estado e execucao | 10-15% | [Exemplo preparado](../examples/03-memoria-estado.md); exercicio nao concluido |
| 4. Avaliacao, analise de erro e ajuste | 15-20% | [Exemplo preparado](../examples/04-avaliacao-planos.md); exercicio nao concluido |
| 5. Coordenacao multiagente | 15-20% | [Exemplo preparado](../examples/05-orquestracao-multiagente.md); exercicio nao concluido |
| 6. Guardrails e prestacao de contas | 10-15% | [Exemplo preparado](../examples/06-guardrails-auditoria.md); exercicio nao concluido |

Fonte dos dominios e pesos: [guia oficial da prova GH-600](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/gh-600).

## Proximo passo concreto

1. Iniciar o [modulo 3 do curso](03-ferramentas-mcp-ambientes.md) em 2026-09-23.
2. Executar o [exemplo do dominio 2](../examples/02-politica-ferramentas.md).
3. Avancar o [exercicio do dominio 2](../exercises/02-ferramentas-ambiente.md) e registrar os aprendizados e duvidas.
