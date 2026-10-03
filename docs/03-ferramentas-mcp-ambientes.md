# Curso - Modulo 3: Ferramentas, MCP e ambientes de execucao

Fonte: [Tooling, MCP, and Agent Execution Environments](https://learn.microsoft.com/en-us/training/modules/agent-tooling-mcp-execution-environments/)

Cobertura da prova: principalmente o **Dominio 2 - Implementar o uso de ferramentas e a interacao com o ambiente**, com fundamentos usados tambem no dominio de guardrails.

Este modulo explica como agentes usam APIs, workflows e ferramentas externas para executar tarefas no GitHub. O foco nao e apenas dar capacidades ao agente, mas delimitar onde ele opera, quais permissoes possui e quais protecoes impedem que uma falha se transforme em uma alteracao insegura.

## Resumo

### 1. APIs e workflows como camada de execucao

Agentes interagem com o GitHub pelos mesmos mecanismos usados por pessoas e automacoes:

- APIs leem o estado do repositorio e executam operacoes;
- branches isolam alteracoes;
- commits registram o trabalho produzido;
- pull requests tornam as mudancas revisaveis;
- GitHub Actions fornece ambientes controlados para testes e automacoes.

Uma execucao tipica parte de uma issue, prompt ou CLI, analisa o repositorio, cria uma branch, produz commits, abre uma pull request e aguarda checks e revisao. Tokens como `GITHUB_TOKEN`, tokens de GitHub App ou PATs determinam quais operacoes sao permitidas e tornam as acoes atribuiveis.

Workflows tradicionais descrevem passos deterministas em YAML. GitHub Agentic Workflows descrevem o resultado desejado em Markdown e usam frontmatter para definir gatilhos, permissoes, ferramentas e saidas seguras. Eles ampliam a automacao para tarefas abertas, mas delimitadas, sem substituir pipelines de CI/CD.

### 2. MCP: servidores, registros e listas de permissao

O Model Context Protocol fornece uma forma padronizada para clientes de IA descobrirem e usarem ferramentas externas.

- **Servidor MCP**: expoe ferramentas e encaminha chamadas ao sistema conectado.
- **Registro MCP**: cataloga servidores disponiveis e padroniza sua descoberta.
- **Allow list**: restringe o uso aos servidores aprovados pela organizacao.

Servidores podem ser locais, quando precisam acessar recursos da maquina ou configuracoes personalizadas, ou remotos, quando se deseja reduzir a instalacao local e compartilhar a integracao entre ambientes.

Os tres elementos resolvem problemas diferentes: o servidor oferece capacidades, o registro facilita descoberta e distribuicao, e a allow list aplica governanca. Conectar um agente a mais ferramentas sem esse controle aumenta o risco de acesso a sistemas sensiveis ou de execucao de acoes indevidas.

### 3. Contexto e boundaries de execucao

O contexto de execucao define onde o agente opera e o que consegue acessar. No GitHub, ele inclui:

- repositorio;
- branch;
- workflow ou job;
- permissoes do token;
- ferramentas disponiveis;
- arquivos ou diretorios no escopo.

O escopo de repositorio e a primeira fronteira. A branch separada impede alteracoes diretas na branch principal. Workflows fornecem ambientes repetiveis e registram logs. Permissoes controlam leitura, escrita, pull requests, secrets e outros recursos.

Custom agents podem restringir ainda mais o foco por arquivos e ferramentas, mas a criacao da branch e o isolamento da execucao pertencem ao ambiente que executa o agente, nao apenas as instrucoes do agente.

### 4. Protecao em profundidade

GitHub Agentic Workflows combinam varias camadas de protecao:

- tokens somente leitura por padrao;
- saidas seguras, aplicadas por uma etapa separada e controlada;
- ausencia de secrets no processo do agente;
- execucao isolada em containers;
- rede isolada e acesso de saida permitido explicitamente;
- deteccao de ameacas antes de operacoes de escrita.

Essas camadas reduzem riscos como excesso de privilegio, prompt injection e alteracoes nao intencionais. A seguranca nao depende de o agente interpretar corretamente uma instrucao; ela precisa ser imposta pelo ambiente.

### 5. Limites da plataforma e revisao humana

O agente deve produzir mudancas em uma branch e apresenta-las para revisao. Regras de repositorio, checks obrigatorios, branch protection e environments definem se o trabalho pode avancar.

Environments podem exigir aprovacao antes de um deploy, restringir secrets e controlar o destino da implantacao. Tambem e importante entender o comportamento dos gatilhos: acoes realizadas com `GITHUB_TOKEN` normalmente nao iniciam novas execucoes, o que ajuda a evitar loops; outras credenciais podem disparar workflows adicionais e exigem cuidado.

### 6. Tratamento de falhas e rastreabilidade

Execucoes confiaveis precisam prever falhas:

- interromper cedo quando uma etapa falha;
- registrar mensagens de erro uteis;
- usar retries apenas para falhas transitorias e de forma limitada;
- manter rollback simples por meio de branches, PRs pequenos e commits reversiveis;
- escalar incertezas ou repeticoes de erro para uma pessoa;
- preservar logs, commits, checks e discussoes para auditoria.

O objetivo e tornar a execucao resiliente, controlada, auditavel e governada por pontos claros de decisao humana.

## Checklist de aprendizado

- [x] Consigo explicar como APIs, branches, PRs e workflows participam de uma execucao agente.
- [x] Sei diferenciar servidor MCP, registro MCP e allow list.
- [x] Consigo definir escopo por repositorio, branch, workflow, permissao e ferramenta.
- [x] Entendo por que instrucoes nao substituem controles tecnicos do ambiente.
- [x] Sei propor tratamento de erro, retry limitado, rollback e escalacao.
- [x] Reconheco quais evidencias tornam uma acao do agente rastreavel.

## Perguntas de revisao

1. Qual e a diferenca entre um workflow tradicional e um Agentic Workflow?
2. Como servidor, registro e allow list MCP trabalham juntos?
3. Quais elementos formam o contexto de execucao de um agente no GitHub?
4. Por que tokens somente leitura e saidas seguras reduzem risco?
5. Quando um retry deve dar lugar a escalacao humana?

## Respostas

1. Um workflow tradicional funciona atraves de um arquivo YAML, em que sao registrados passos deterministicos a serem realizados pelas actions. Enquanto isso, um Agentic Workflow e definido em um arquivo Markdown, com o objetivo escrito em linguagem natural e os gatilhos, permissoes, ferramentas e saidas seguras definidos pelo frontmatter. Esse arquivo e compilado em um workflow do GitHub Actions, permitindo raciocinio contextual dentro dos limites declarados, sem depender apenas das instrucoes para garantir a seguranca da execucao.

2. O servidor MCP expoe as ferramentas e encaminha o seu uso a servicos externos de forma padronizada, enquanto o registro cataloga os servidores disponiveis e facilita sua descoberta. A allow list restringe quais servidores MCP podem ser usados dentro de uma organizacao. Assim, o servidor oferece a capacidade, o registro permite encontra-la e a allow list aplica o limite de uso.

3. Repositorio, branch, workflow ou job, permissoes do token, ferramentas disponiveis e arquivos ou diretorios dentro do escopo. Esses elementos definem onde o agente pode operar, quais informacoes pode acessar e quais acoes pode executar.

4. Tokens somente leitura impedem que o agente altere diretamente areas sensiveis do projeto. As saidas seguras limitam a escrita a operacoes declaradas e validadas por uma etapa controlada, unificando a forma como os agentes finalizam o trabalho. Essa separacao reduz o privilegio e o impacto de uma instrucao maliciosa ou de uma decisao incorreta.

5. O retry deve dar lugar a escalacao humana quando as tentativas limitadas nao resolvem a falha, quando o erro nao e transitorio ou quando envolve permissao, seguranca, politica ou uma decisao de alto impacto. A repeticao so deve ser usada para falhas que podem desaparecer sem mudar a tarefa; insistir em um erro deterministico apenas repete o problema e pode aumentar o risco.

## Duvida resolvida

**Workflows e environments sao equivalentes?** Nao. O workflow coordena jobs; o runner ou container fornece os recursos de execucao; e o GitHub Environment aplica aprovacoes, secrets e protecoes. O agente usa apenas os recursos, ferramentas e permissoes liberados para seu job.

## Relacao com o GH-600

Este modulo cobre a base pratica do dominio de ferramentas e ambiente: selecao e permissao de ferramentas, configuracao de MCP, escopo de execucao, caminhos seguros, tratamento de falhas e rastreabilidade.
