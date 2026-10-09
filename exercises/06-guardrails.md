# Dominio 6 - Guardrails e prestacao de contas

Peso na prova: **10-15%**.

Modulo principal do curso: [Governance, Guardrails, and Operations](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/).

## Tarefa

Defina controles para um agente que pode ler o repositorio, propor alteracoes e executar validacoes.

## Entregavel

- Permissoes e limites.
- Acoes que exigem aprovacao humana.
- Logs ou artefatos de auditoria.
- Riscos e mitigacoes.

## Reflexao

- O que acontece quando uma ferramenta retorna dados inesperados?
- Como explicar e rastrear uma decisao do agente?

## Entrega

### Permissoes e limites

Esse agente deve ter acesso de leitura a codigo e issues por padrao, gerando artefatos da sua pesquisa para revisao. O token de leitura nao ganha escrita por conta propria: os jobs que precisam propor mudancas recebem permissoes adicionais, limitadas ao necessario.

Para propor alteracoes, ele deve atuar em uma branch isolada, apenas nos caminhos permitidos, registrar as mudancas em commits e abrir uma PR para a branch principal. Branch protection e rulesets exigem PR, checks e revisoes, sem permitir que o agente faca push direto ou contorne essas exigencias. O limite de caminhos precisa de validacao ou controle proprio; uma branch isolada, sozinha, nao restringe os arquivos que podem ser alterados.

Para validacoes, o agente deve ter o menor privilegio possivel, executar apenas comandos e workflows autorizados, com limites de tempo e em ambiente isolado. Nao deve receber acesso desnecessario a secrets nem permissao para merge ou deploy em producao.

### Aprovacao humana

As mudancas propostas precisam de review humano antes do merge. O CODEOWNERS indica os responsaveis, e as regras do repositorio devem tornar a aprovacao obrigatoria. Alteracoes em workflows, infraestrutura, seguranca ou acesso a secrets exigem aprovacao explicita antes da acao de risco.

Qualquer deploy em producao fica fora da autonomia deste agente: se necessario, deve ocorrer por um fluxo separado, com environment protegido, aprovacao humana e plano de rollback. A aprovacao nao concede permissoes amplas ao agente automaticamente.

### Evidencias de auditoria

As execucoes devem gerar logs e artefatos revisaveis, registrando:

- issue ou tarefa, PR e SHA do commit;
- identidade do agente ou ator e horario da execucao;
- acao, alvo, regra aplicada e motivo de permitir ou bloquear;
- resultados dos checks, limitacoes e tentativas de recuperacao;
- aprovacoes humanas e links dos workflows.

Essas evidencias ajudam a identificar quem fez o que e por que, sem expor tokens, secrets ou dados sensiveis. A retencao deve ser suficiente para auditoria e resposta a incidentes; evidencia obrigatoria ausente deve bloquear o avancamento.

### Riscos e mitigacoes

- Permissoes excessivas: usar menor privilegio por job e separar tarefas de leitura das que precisam escrever.
- Mudanca fora do escopo: validar os caminhos e o diff antes de encaminhar a PR para aprovacao.
- Conteudo externo com instrucoes maliciosas: tratar como dado nao confiavel, sem permitir que altere as instrucoes ou amplie permissoes.
- Falhas repetidas: permitir no maximo duas novas tentativas para falhas transitorias, registrando cada uma; se persistirem, parar e escalar.
- Falhas de seguranca, permissao ou erros nao transitorios: parar e escalar imediatamente, sem repetir a mesma acao nem ampliar acesso automaticamente.
- Vazamento em logs ou artefatos: evitar registrar dados sensiveis e revisar as evidencias antes de compartilha-las.

### Reflexao feita

Quando uma ferramenta retorna dados inesperados, o agente deve validar o formato, a origem e a coerencia com a tarefa antes de usar o resultado. Se nao conseguir validar, deve marcar a informacao como nao verificada e interromper a etapa que depende dela. Uma nova tentativa so cabe se a falha for transitoria e dentro do limite; sinais de seguranca exigem escalacao imediata.

Para explicar e rastrear uma decisao, o agente deve registrar o objetivo, as evidencias usadas, a regra aplicada, o resultado e o proximo passo, vinculando tudo a tarefa, ao SHA e a execucao do workflow. Isso facilita identificar a causa e mitigar o problema, sem depender apenas do historico da conversa.

Fontes oficiais: [menor privilegio](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/5-control-agent-capabilities), [evidencias e auditoria](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/6-make-actions-observable-traceable-auditable) e [governanca e recuperacao](https://learn.microsoft.com/en-us/training/modules/governance-guardrails-operations/7-maintain-governance-operational-reliability).
