# Estado da trilha

Atualizado em: 2026-10-15

## Convencao

O progresso e registrado em duas dimensoes:

- **modulos do curso**: definem a ordem de leitura dos resumos;
- **dominios da prova**: definem a cobertura e os exercicios praticos.

Consulte o [mapa entre curso e prova](roadmap.md#mapa-entre-curso-e-prova). As duas sequencias nao sao equivalentes.

## Progresso do curso

Curso GH-600T00-A concluido em 2026-10-07, com os seis modulos estudados. A primeira revisao dos seis dominios e os seis exercicios foram concluidos em 2026-10-09. A revisao final dos seis dominios foi concluida em 2026-10-15, encerrando os estudos neste repositorio.

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

#### Curso - Modulo 3: Ferramentas, MCP e ambientes de execucao

- Resumo: [docs/03-ferramentas-mcp-ambientes.md](03-ferramentas-mcp-ambientes.md)
- Fonte: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/agent-tooling-mcp-execution-environments/)
- Foco: APIs, workflows, MCP, allow lists, contexto, limites e protecoes de execucao.
- Status: concluido em 2026-09-27 e revisado em 2026-09-29; exercicio do dominio 2 concluido em 2026-09-29.

#### Curso - Modulo 4: Sistemas multiagente e orquestracao

- Resumo: [docs/04-sistemas-multiagente-orquestracao.md](04-sistemas-multiagente-orquestracao.md)
- Fonte: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/multi-agent-systems-orchestration/)
- Foco: responsabilidades, isolamento, handoffs, conflitos, observabilidade e recuperacao.
- Status: concluido em 2026-10-01 e revisado em 2026-10-04; exercicio do dominio 5 concluido.
- Reforco concluido na revisao final em 2026-10-15: retry limitado, rollback e escalacao, com checklist do resumo completo.

#### Curso - Modulo 5: Memoria, estado e avaliacao

- Resumo: [docs/05-memoria-estado-avaliacao.md](05-memoria-estado-avaliacao.md)
- Fonte: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/)
- Cobertura da prova: dominios 3 e 4.
- Status: concluido em 2026-10-04; revisao e exercicios dos dominios 3 e 4 concluidos em 2026-10-06, com perguntas respondidas e checklist marcado.
- Aprendizado reforcado: criterios de sucesso definem expectativas; sinais fornecem evidencias; quality gates aplicam regras de aceitacao. A classificacao da falha orienta o ajuste, que precisa ser validado novamente.
- Evidencias de estudo: tabela de memoria e estado e cinco casos de avaliacao de planos com falhas simuladas; isso nao representa execucao real de testes ou scans.

#### Curso - Modulo 6: Governanca, guardrails e operacoes

- Resumo: [docs/06-governanca-guardrails-operacoes.md](06-governanca-guardrails-operacoes.md)
- Fonte: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/)
- Cobertura da prova: principalmente dominio 6, com aplicacao transversal.
- Status: concluido em 2026-10-07; revisao e exercicio do dominio 6 concluidos em 2026-10-09, com perguntas respondidas e checklist marcado.
- Evidencia pratica: [exercicio do dominio 6](../exercises/06-guardrails.md), com permissoes por job, aprovacoes humanas, evidencias de auditoria, riscos e regras de recuperacao.
- Aprendizado reforcado: permissoes limitam a capacidade real; guardrails aplicam restricoes tecnicas; falhas de seguranca e permissao exigem parada e escalacao, nao retries automaticos.

### Primeira revisao do Dominio 1 concluida

Dominio 1 - Preparar a arquitetura do agente e os processos do SDLC

- Cobertura conjunta dos modulos 1 e 2 revisada.
- [Exercicio do dominio 1](../exercises/01-arquitetura-sdlc.md) retomado e conceitos principais conferidos.
- Primeira revisao concluida em 2026-09-22, com [exemplo pratico](../examples/01-fluxo-agente-sdlc.md).

### Duvidas resolvidas durante a revisao

- Registrada a diferenca entre `CODEOWNERS`, rulesets e protecao de branch no [resumo do modulo 2](02-arquitetura-agente-integracao.md#dúvida-resolvida-qual-é-a-diferença-entre-codeowners-rulesets-e-proteção-de-branch).
- Aprendizado principal: `CODEOWNERS` define quem deve revisar; rulesets e protecao de branch definem as condicoes impostas pela plataforma.
- Registrada a diferenca entre workflow, runner e environment no [resumo do modulo 3](03-ferramentas-mcp-ambientes.md#duvida-resolvida).
- O padrao fan-out/fan-in aparece na secao de [orquestracao por eventos e artefatos do modulo 4](04-sistemas-multiagente-orquestracao.md#2-orquestracao-por-eventos-e-artefatos).

### Atividade complementar concluida

Casos de uso de IA para desenvolvedores com GitHub Copilot

- Modulo: [Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/developer-use-cases-for-ai-with-github-copilot/)
- Duracao: 49 minutos, em 7 unidades.
- Relacao principal: complemento ao dominio 1 da prova e ao estudo do SDLC iniciado nos modulos 1 e 2 do curso.
- Foco: produtividade, preferencias do desenvolvedor, uso de IA nas etapas do SDLC, limitacoes e medicao de impacto.
- Status: concluido em 2026-09-22.

## Cobertura da prova

| Dominio | Peso | Estado |
| --- | --- | --- |
| 1. Arquitetura e processos do SDLC | 15-20% | Revisao final concluida em 2026-10-15; modulos 1 e 2 concluidos e [exemplo preparado](../examples/01-fluxo-agente-sdlc.md) |
| 2. Ferramentas e ambiente | 20-25% | Revisao final concluida em 2026-10-15; modulo 3 e [exercicio](../exercises/02-ferramentas-ambiente.md) concluidos; [exemplo preparado](../examples/02-politica-ferramentas.md) |
| 3. Memoria, estado e execucao | 10-15% | Revisao final concluida em 2026-10-15; modulo 5 revisado e [exercicio](../exercises/03-memoria-estado.md) concluido; [exemplo preparado](../examples/03-memoria-estado.md) |
| 4. Avaliacao, analise de erro e ajuste | 15-20% | Revisao final concluida em 2026-10-15; modulo 5 revisado e [exercicio](../exercises/04-avaliacao-ajuste.md) concluido; [exemplo preparado](../examples/04-avaliacao-planos.md) |
| 5. Coordenacao multiagente | 15-20% | Revisao final concluida em 2026-10-15; modulo 4 revisado e [exercicio](../exercises/05-multiagente.md) concluido; checklist de retry, rollback e escalacao concluido; [exemplo preparado](../examples/05-orquestracao-multiagente.md) |
| 6. Guardrails e prestacao de contas | 10-15% | Revisao final concluida em 2026-10-15; modulo 6 revisado e [exercicio](../exercises/06-guardrails.md) concluido; [exemplo preparado](../examples/06-guardrails-auditoria.md) |

Fonte dos dominios e pesos: [guia oficial da prova GH-600](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/gh-600).

## Encerramento dos estudos

- [x] Revisao final dos seis dominios da prova concluida em 2026-10-15, conforme confirmacao do estudante.
- [x] Seis modulos do curso e seis checkpoints concluidos.
- [x] Reforco de retry limitado, rollback e escalacao concluido no [modulo 4](04-sistemas-multiagente-orquestracao.md).

Nao ha proximo passo de estudo pendente neste repositorio. Os resumos, checkpoints e [exemplos dos seis dominios](../examples/README.md) ficam disponiveis para consulta.
