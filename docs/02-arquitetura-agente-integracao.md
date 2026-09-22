# Curso - Módulo 2: Arquitetura do agente e integração com o SDLC

Fonte: [Designing Agent Architecture and SDLC Integration](https://learn.microsoft.com/en-gb/training/modules/design-agent-architecture-integration/)

Cobertura da prova: principalmente o **Domínio 1: preparar a arquitetura do agente e os processos do SDLC**, com conceitos que também aparecem nos domínios de ferramentas e guardrails.

O módulo trata a arquitetura do agente como parte do ciclo de desenvolvimento de software. Em vez de pensar no agente como um chatbot isolado, é preciso definir responsabilidades, entradas, saídas, critérios de sucesso e controles de governança.

## Resumo

### 1. Responsabilidades do agente no SDLC

O agente pode participar de diferentes etapas do ciclo de vida, desde que cada responsabilidade tenha limites claros. Ele pode:

- compreender e decompor requisitos;
- planejar tarefas e dependências;
- implementar alterações em código ou configuração;
- validar resultados com testes e outras verificações;
- preparar pull requests e evidências da entrega;
- acompanhar a operação e apoiar a manutenção.

O agente assume tarefas bem delimitadas, mas não substitui decisões humanas. Revisão, aprovação e responsabilidade pelo resultado continuam fazendo parte do processo.

### 2. Entradas, saídas e critérios de sucesso

Uma tarefa confiável precisa definir:

- o objetivo;
- o contexto necessário;
- as entradas disponíveis;
- as saídas esperadas;
- as restrições;
- os critérios de sucesso;
- as evidências que comprovarão o resultado.

Sem essas definições, o agente precisa preencher lacunas por conta própria. Isso aumenta a chance de erro, desvio de escopo e resultados difíceis de verificar.

### 3. Planejamento, raciocínio e execução

A arquitetura deve separar três responsabilidades:

- **planejamento:** identificar etapas, dependências e restrições;
- **raciocínio:** interpretar o contexto e escolher uma abordagem;
- **execução:** usar ferramentas para alterar arquivos, executar testes e registrar resultados.

Essa separação permite analisar o plano antes de liberar ações. Também facilita a identificação de falhas, pois fica mais simples distinguir um plano inadequado, uma decisão incorreta e um problema no uso da ferramenta.

### 4. Governança por pull request

O GitHub concentra revisão, validação e aprovação. Uma arquitetura segura pode combinar:

- templates de pull request;
- verificações de CI e qualidade;
- CODEOWNERS;
- rulesets e proteção de branch;
- environments com aprovação;
- revisão humana obrigatória.

Esses controles impedem que uma alteração avance sem contexto, validação ou autorização. A pull request também reúne o plano, as mudanças, as evidências e o feedback em um único lugar.

#### Dúvida resolvida: qual é a diferença entre CODEOWNERS, rulesets e proteção de branch?

Os três recursos se complementam, mas têm responsabilidades diferentes:

| Recurso | Responsabilidade | Exemplo |
| --- | --- | --- |
| `CODEOWNERS` | Define quem é responsável por determinados arquivos ou diretórios. | Mudanças em `/infra/` solicitam revisão de `@org/platform`. |
| Proteção de branch | Define condições para alterar ou fazer merge em branches importantes. | A branch `main` exige pull request, duas aprovações e checks aprovados. |
| Rulesets | Agrupam políticas aplicáveis a branches, tags ou pushes, com alvos e exceções configuráveis. | As branches `release/*` exigem commits assinados e bloqueiam force push. |

O arquivo `CODEOWNERS` identifica os revisores relacionados aos caminhos alterados e solicita sua revisão automaticamente. Sozinho, ele não torna essa aprovação obrigatória. Para bloquear o merge sem a aprovação de um code owner, é necessário habilitar esse requisito em uma regra de proteção de branch ou em um ruleset.

A proteção de branch é o mecanismo tradicional para exigir pull requests, aprovações, status checks, histórico linear, commits assinados e outras condições. Quando mais de uma regra de proteção corresponde à mesma branch, apenas uma delas é aplicada.

Rulesets oferecem uma forma mais ampla e combinável de aplicar políticas. Vários rulesets podem atingir o mesmo alvo; suas regras são agregadas, e a versão mais restritiva prevalece quando houver sobreposição. Rulesets e proteções de branch também podem coexistir, caso em que todas as regras aplicáveis são consideradas.

Em resumo: `CODEOWNERS` responde **quem deve revisar**, enquanto proteção de branch e rulesets respondem **quais condições a plataforma deve impor**. Para novas configurações mais complexas ou reutilizáveis, rulesets tendem a oferecer maior flexibilidade; a proteção de branch continua adequada para regras simples ou configurações existentes.

Fontes oficiais:

- [About code owners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
- [About protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
- [About rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)

### 5. Saídas, contexto, gatilhos e handoffs

Em fluxos maiores, o trabalho pode ser dividido em etapas ou agentes. Para isso, cada etapa precisa produzir uma saída clara para a próxima:

- artefatos e saídas estruturadas carregam o resultado;
- o contexto explica objetivo, decisões e restrições;
- gatilhos determinam quando a próxima etapa começa;
- handoffs registram a transferência de responsabilidade.

Essa organização reduz o acoplamento entre etapas e facilita depuração, revisão e auditoria. O fluxo não deve depender de informações que existam apenas em uma conversa temporária.

### 6. Operação e controle

Uma arquitetura de agente também precisa definir como a execução será controlada. Isso inclui:

- logs, métricas e artefatos para observabilidade;
- permissões e governança das ferramentas;
- integração com ferramentas externas por MCP;
- limites para secrets e recursos sensíveis;
- hooks e verificações de segurança;
- restrições de rede;
- tratamento de erros, retries limitados e caminhos de recuperação.

O ambiente deve impor os limites. Instruções ajudam a orientar o agente, mas não substituem permissões, isolamento, checks e aprovações.

## Checklist de aprendizado

- [x] Consigo mapear as responsabilidades do agente para as etapas do SDLC.
- [x] Sei distinguir objetivo, contexto, entrada, saída e critério de sucesso.
- [x] Entendo a diferença entre planejamento, raciocínio e execução.
- [x] Reconheço o papel de pull requests, checks e regras de branch na governança.
- [x] Sei explicar como fluxos observáveis reduzem riscos.
- [x] Entendo por que permissões, secrets e limites de ferramentas fazem parte da arquitetura.

## Perguntas de revisão

1. Qual é a vantagem de separar planejamento, raciocínio e execução?
2. Como pull requests e regras do repositório ajudam a governar o trabalho do agente?
3. O que deve fazer parte de um critério de sucesso bem definido?
4. Qual é a função das saídas, do contexto e dos handoffs em um fluxo de trabalho?
5. Como a observabilidade e os limites de acesso reduzem o risco operacional?

## Respostas

1. A principal vantagem é conseguir visualizar o objetivo inicial, o passo a passo que será executado, como o trabalho foi feito e o que ele gerou. Isso ajuda a manter a consistência ao longo do fluxo e permite que haja validação humana antes que o código seja alterado de fato. Também facilita a identificação da etapa que gerou uma possível falha.

2. Pull requests e regras do repositório fazem com que o agente trabalhe como um contribuidor, com suas alterações sujeitas a checks e revisão. Isso garante que haja validação humana antes de a implementação seguir adiante e evita impactos não mapeados em código produtivo ou crítico.

3. Um critério de sucesso bem definido deve incluir o objetivo a ser atingido, o escopo e as restrições das alterações, as condições de aceite, os testes e as validações verificáveis, além dos artefatos que precisam ser gerados.

4. As saídas evidenciam os resultados do fluxo de trabalho e levam essas informações para a próxima etapa. O contexto descreve o objetivo, as decisões e as restrições do trabalho. Os handoffs fazem a passagem de conhecimento, estado e responsabilidade entre agentes ou etapas do fluxo, ajudando a manter sua consistência.

5. A observabilidade é fundamental para identificar e investigar possíveis falhas ou comportamentos estranhos que possam gerar riscos à operação do sistema. Os limites de acesso restringem o que os agentes podem fazer e ajudam a impedir que ações de maior impacto ocorram sem validação humana, reduzindo o risco operacional.

## Relação com o GH-600

O módulo transforma os fundamentos anteriores em decisões de arquitetura. Ele mostra que a confiabilidade de um agente depende tanto da capacidade do modelo quanto da organização do fluxo, das permissões e dos controles do repositório.
