# Curso - Modulo 6: Governanca, guardrails e operacoes

Fonte: [Governance, Guardrails, and Operations](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/)

Cobertura da prova: principalmente o **Dominio 6 - Implementar guardrails e prestacao de contas**, com aplicacao transversal aos demais dominios.

Este modulo mostra como transformar principios de seguranca em controles executaveis. A autonomia do agente deve acompanhar o risco da acao, enquanto regras do GitHub, menor privilegio, aprovacoes humanas e evidencias garantem que o sistema continue controlavel ao longo do tempo.

## Resumo

### 1. Autonomia baseada em risco

Nem toda acao precisa do mesmo nivel de controle. O risco depende do impacto, do ambiente atingido e da facilidade de reversao.

Um modelo pratico de autonomia inclui:

- **somente leitura**: inspecionar, resumir e recomendar;
- **somente propor**: criar branch e PR, sem merge ou deploy;
- **executar com guardrails**: rodar workflows pre-aprovados dentro de limites;
- **execucao autorizada por pessoa**: realizar acoes criticas apenas depois de aprovacao.

Documentacao e formatacao tendem a ser reversiveis. Alteracoes em workflows, infraestrutura, seguranca, secrets ou producao devem ser tratadas como alto risco. O nivel de risco deve ser um sinal estruturado usado pelo workflow, nao apenas uma justificativa narrativa.

Autonomia pode crescer de forma progressiva conforme o comportamento se mostra confiavel, mas capacidades de alto impacto continuam cercadas por gates.

### 2. Controles nativos e enforcement em camadas

Governanca precisa ser aplicada pela plataforma:

- rulesets e branch protection;
- pull request obrigatoria;
- required checks;
- CODEOWNERS e revisoes obrigatorias;
- environments com aprovacao;
- restricao de push direto, force push e delecao;
- hooks que bloqueiam comandos perigosos antes da execucao;
- guardrail workflows para regras adicionais.

Uma politica apenas documentada pode ser ignorada. Controles efetivos operam antes da acao com permissoes, durante a acao com validacoes e depois da acao com logs e artefatos.

### 3. Human-in-the-loop nos pontos certos

O objetivo nao e aprovar cada passo, mas inserir julgamento humano onde a consequencia e maior:

- merge de mudancas relevantes;
- deploy em producao;
- acesso a secrets;
- alteracoes em infraestrutura, workflows ou seguranca;
- decisoes que nao podem ser verificadas apenas por checks.

Um fluxo tipico faz o agente abrir a PR com plano e risco, executa checks, solicita os owners adequados e permite merge somente depois das aprovacoes.

Para evitar fadiga de governanca, revisoes devem receber evidencias claras, PRs pequenos, ownership correto e plano de rollback. Aprovacoes repetitivas que nao reduzem risco devem ser removidas.

### 4. Menor privilegio

Permissoes definem o poder real do agente, independentemente de sua intencao. Um token amplo transforma um erro pequeno em um incidente maior.

O padrao deve ser somente leitura, com elevacao apenas no job que precisa escrever. Tambem e necessario:

- restringir secrets por environment;
- separar jobs de baixo e alto risco;
- conceder escrita apenas para o recurso necessario;
- limitar acoes de terceiros e fixar versoes quando possivel;
- revisar periodicamente tokens e permissoes.

Menor privilegio reduz o blast radius e facilita contencao e recuperacao.

### 5. Evidencia, rastreabilidade e auditoria

Toda acao relevante deve deixar uma trilha:

- PR e historico de commits;
- ator, tempo e logs do workflow;
- plano, testes, scans e relatorio de execucao como artefatos;
- eventos de aprovacao e merge;
- registro de aprovacao do environment.

Workflows criticos devem operar com evidence-first: ausencia da evidencia esperada e uma falha, nao um detalhe opcional. A retencao precisa ser suficiente para auditoria e resposta a incidentes.

### 6. Governanca continua e confiabilidade operacional

Governanca nao termina na configuracao inicial. Regras podem perder efeito quando checks mudam de nome, permissoes crescem, CODEOWNERS fica desatualizado ou secrets migram para escopos mais amplos.

A operacao deve incluir:

- ownership e ciclo de vida claro para cada agente;
- runbooks e cadencia de revisao;
- monitoramento de falhas e violacoes;
- auditoria periodica de rulesets, permissoes e environments;
- retries limitados para falhas transitorias;
- escalacao para falhas repetidas;
- rollback por mudancas pequenas e reversiveis;
- aposentadoria de agentes sem perder o historico.

Antes da execucao, tarefas autonomas devem ter criterio de aceite, restricoes, non-goals, caminhos permitidos e estrategia de validacao. Ambiguidade deve ser resolvida antes de se tornar risco operacional.

### 7. Antipadroes de governanca

Alguns sinais de alerta sao:

- autonomia sem limites para acoes irreversiveis;
- tokens com escrita ampla e acesso desnecessario a secrets;
- evidencias apenas em logs temporarios;
- caminhos que contornam PRs e checks;
- aprovacoes feitas apenas para desbloquear o fluxo;
- repeticao automatica de falhas de seguranca;
- ownership ou politicas que nao acompanham a evolucao do sistema.

Guardrails eficazes combinam enforcement tecnico, evidencia suficiente e responsabilidade humana explicita.

## Checklist de aprendizado

- [x] Consigo classificar acoes por risco, impacto e reversibilidade.
- [x] Sei associar niveis de autonomia a controles tecnicos.
- [x] Entendo como rulesets, checks, CODEOWNERS e environments aplicam governanca.
- [x] Sei posicionar aprovacoes humanas sem criar bloqueios desnecessarios.
- [x] Consigo definir permissoes de menor privilegio por workflow e job.
- [x] Sei especificar evidencias para auditoria e resposta a incidentes.
- [x] Entendo por que governanca precisa de revisao e manutencao continuas.

## Perguntas de revisao

1. Por que autonomia deve ser determinada por risco e reversibilidade?
2. Qual e a diferenca entre uma politica documentada e um guardrail efetivo?
3. Onde a revisao humana gera mais valor?
4. Por que permissoes definem o limite real do agente?
5. O que caracteriza um workflow evidence-first?
6. Como detectar governance drift?

## Respostas

1. Isso ocorre pois nem toda acao precisa ter o mesmo nivel de controle. Quanto maior for o impacto no software/negocio/usuario e mais dificil for reverter a acao, mais camadas de validacao e aprovacao sao necessarias, dividindo responsabilidades e reduzindo riscos. Tarefas de baixo risco e facilmente reversiveis, como ajustes de documentacao, podem seguir de forma mais autonoma, enquanto refatoracoes simples ainda podem exigir PR e checks. Complexidade nao e sinonimo de risco: uma pequena alteracao em workflow pode ter um impacto alto.

2. Enquanto uma politica documentada, apesar de guiar o funcionamento, pode ser ignorada por agente ou usuario, um guardrail efetivo aplica tecnicamente as restricoes, exigindo que certos criterios sejam atendidos para seguir. Por exemplo, uma regra que bloqueia o merge sem um check obrigatorio aprovado transforma a politica em um controle efetivo.

3. A revisao humana gera mais valor em pontos criticos do SDLC, em que os checks nao sao suficientes para tomar uma decisao, como deploy em producao, acesso a secrets e alteracoes em infraestrutura ou seguranca. Ela acrescenta julgamento sobre riscos e contexto e deixa a responsabilidade pela aprovacao explicita, mas nao garante ausencia de erros nem precisa ocorrer em cada passo de baixo risco.

4. Isso ocorre pois as permissoes definem de forma efetiva o que o agente pode acessar ou executar, independentemente da sua intencao ou das instrucoes recebidas. Elas nao apenas sugerem comportamentos: restringem sua capacidade real. Aplicar menor privilegio limita o impacto de erros, mas a governanca tambem depende de checks, aprovacoes e evidencias.

5. E caracterizado por tratar toda ausencia da evidencia esperada como uma falha, nao um detalhe opcional. Ou seja, toda acao relevante deve deixar uma trilha, com referencias como SHA do commit, ator, horario, resultados dos checks, artefatos e aprovacoes quando exigidas. A retencao precisa ser suficiente para auditoria e resposta a incidentes.

6. Podemos detectar isso acompanhando de forma continua o comportamento dos agentes e as execucoes dos workflows, mas tambem revisando periodicamente se os controles configurados continuam de acordo com as politicas. Sinais de governance drift incluem checks obrigatorios removidos ou renomeados, permissoes ampliadas, CODEOWNERS desatualizado, exigencias de revisao reduzidas e secrets movidos para escopos mais amplos. Mesmo que os resultados parecam corretos, os controles podem ter perdido sua eficacia.

## Relacao com o GH-600

Este modulo consolida autonomia, enforcement, aprovacao humana, menor privilegio, observabilidade e operacao continua. Esses controles sustentam a prestacao de contas e limitam o impacto de falhas em qualquer arquitetura de agentes.
