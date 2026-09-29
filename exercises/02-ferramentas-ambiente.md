# Dominio 2 - Ferramentas e interacao com o ambiente

Peso na prova: **20-25%**.

Modulo principal do curso: [Tooling, MCP, and Agent Execution Environments](https://learn.microsoft.com/en-us/training/modules/agent-tooling-mcp-execution-environments/).

Status: concluido em 2026-09-29.

## Tarefa

Defina as ferramentas de um agente de pesquisa e de um agente implementador.

1. Agente de pesquisa:

   - Deve ter ferramenta de leitura e pesquisa dentro do repositorio, capacidade de visualizar o contexto geral, e navegar pelas issues e conteudos
   - Ter permissao de read-only
   - Sem permissao de editar

    Exemplo = Ler um bug apontado em uma issue, ler o contexto do repositorio, encontrar o problema no codigo e propor um plano de solucao.

2. Agente implementador:

    - Ferramentas disponiveis de ler e editar arquivos, verificar checks da pipe, gerar pull requests e branchs, acesso a ferramentas externas via mcp
    - Ter permissao de editar, modificar, gerar branchs e rodar cheks
    - Ser negado para mexer em branchs protegidas, implantar em ambiente produtivo, acessar secrets

    Exemplo = A partir de um plano definido, criar uma branch, realizar modificacoes no codigo e abrir um PR para propor mudancas na main

## Entregavel

- Lista de ferramentas por agente.
- Permissoes permitidas e negadas.
- Exemplo de uma tarefa que cada agente pode executar.

## Reflexao

- O que deve ser somente leitura?
Momentos em que ainda nao se tem um definicao certa sobre o que vai ser feito, e/ou configuracoes criticas que afetam o codigo em producao
- Quando uma acao exige aprovacao?
Quando ela impacta diretamente o usuario, ou houve falha do agente que necessite de revisao
