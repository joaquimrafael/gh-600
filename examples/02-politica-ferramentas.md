# Exemplo do Dominio 2 - Politica de ferramentas e permissoes

## Problema

Um agente de pesquisa precisa consultar o repositorio, enquanto um agente implementador precisa propor mudancas. Dar as mesmas ferramentas e permissoes aos dois aumenta o impacto de um erro.

## Politica de exemplo

O YAML abaixo e um modelo de decisao para o exercicio, nao um arquivo de configuracao consumido diretamente pelo GitHub:

```yaml
agents:
  researcher:
    tools:
      - repository.search
      - repository.read_file
      - issues.read
    allow:
      - read repository content
      - read issues and pull requests
    deny:
      - modify files
      - create or merge pull requests
      - access secrets

  implementer:
    tools:
      - repository.read_file
      - repository.edit_file
      - checks.run
      - pull_requests.create
    allow:
      - edit files under src/ and tests/
      - create a task branch
      - run approved checks
      - open a pull request
    deny:
      - push to main
      - merge a pull request
      - deploy to production
      - access secrets
```

## Casos para reproduzir

| Solicitacao | Agente | Decisao esperada | Motivo |
| --- | --- | --- | --- |
| Localizar onde a autenticacao e validada | `researcher` | Permitir | Usa apenas busca e leitura. |
| Corrigir um teste em `tests/auth/` | `implementer` | Permitir em branch isolada | Caminho e operacao estao no escopo. |
| Alterar `.github/workflows/deploy.yml` | `implementer` | Bloquear e escalar | O caminho nao esta na lista permitida. |
| Ler um secret para diagnosticar uma falha | Qualquer agente | Bloquear | Secrets nao pertencem ao contexto do agente. |
| Fazer merge depois dos checks | `implementer` | Bloquear e solicitar aprovacao | O agente pode propor, mas nao aceitar a propria mudanca. |

## Como executar o exercicio

1. Leia cada solicitacao da tabela.
2. Compare operacao, ferramenta e caminho com a politica YAML.
3. Registre `permitir`, `bloquear` ou `escalar` antes de considerar o objetivo da tarefa.
4. Verifique se sua decisao coincide com a coluna de resultado esperado.

## O que observar

- O nome do agente nao concede capacidade; ferramentas e permissoes concedem.
- Uma ferramenta permitida ainda precisa respeitar limites de caminho e operacao.
- A instrucao do usuario nao substitui um bloqueio imposto pelo ambiente.
- A escalacao e uma saida valida quando a tarefa exige autoridade adicional.

## Melhoria possivel

Converter a politica conceitual em permissoes de workflow, regras de caminhos e uma allow list de servidores MCP aprovados.

Fonte oficial: [Tooling, MCP, and Agent Execution Environments](https://learn.microsoft.com/en-us/training/modules/agent-tooling-mcp-execution-environments/).
