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

- [ ] Consigo mapear as responsabilidades do agente para as etapas do SDLC.
- [ ] Sei distinguir objetivo, contexto, entrada, saída e critério de sucesso.
- [ ] Entendo a diferença entre planejamento, raciocínio e execução.
- [ ] Reconheço o papel de pull requests, checks e regras de branch na governança.
- [ ] Sei explicar como fluxos observáveis reduzem riscos.
- [ ] Entendo por que permissões, secrets e limites de ferramentas fazem parte da arquitetura.

## Perguntas de revisão

1. Qual é a vantagem de separar planejamento, raciocínio e execução?
2. Como pull requests e regras do repositório ajudam a governar o trabalho do agente?
3. O que deve fazer parte de um critério de sucesso bem definido?
4. Qual é a função das saídas, do contexto e dos handoffs em um fluxo de trabalho?
5. Como a observabilidade e os limites de acesso reduzem o risco operacional?

## Respostas

1. A separação permite revisar o plano antes da execução, localizar a origem de uma falha e ajustar cada etapa sem tratar todo o fluxo como uma única ação opaca.

2. Eles definem as condições para aceitar uma alteração. Checks, proteção de branch, CODEOWNERS e revisões obrigatórias impedem que o trabalho avance sem validação ou autorização.

3. O critério deve descrever o resultado esperado, as condições de aceite, as restrições, as verificações necessárias e as evidências que demonstram a conclusão da tarefa.

4. As saídas levam resultados de uma etapa para outra, o contexto preserva objetivo e decisões, e os handoffs deixam claro quem ou qual processo assume o trabalho em seguida.

5. A observabilidade permite reconstruir a execução e investigar falhas. Limites de acesso reduzem o que o agente pode afetar caso algo saia errado.

## Relação com o GH-600

O módulo transforma os fundamentos anteriores em decisões de arquitetura. Ele mostra que a confiabilidade de um agente depende tanto da capacidade do modelo quanto da organização do fluxo, das permissões e dos controles do repositório.
