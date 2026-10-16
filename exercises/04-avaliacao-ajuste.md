# Dominio 4 - Avaliacao, analise de erro e ajuste

Peso na prova: **15-20%**.

Modulo principal do curso: [Memory, State, and Evaluation](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/).

## Tarefa

Crie cinco casos de avaliacao para um agente que prepara um plano de implementacao.

## Entregavel

- Entrada esperada de cada caso.
- Resultado considerado correto.
- Falha observada ou simulada.
- Ajuste proposto.

## Reflexao

- Como medir qualidade, seguranca e consistencia?
- Que erro deve bloquear a entrega?

## Resposta

Os casos abaixo avaliam o plano produzido pelo agente antes da implementacao. As falhas sao simuladas, nao resultados de execucoes reais.

### 1. Suite de testes

- Entrada: demanda para alterar uma validacao, com criterios de aceite, testes existentes e regra de cobertura do repositorio.
- Resultado correto: o plano inclui testes para o comportamento esperado, erros e regressao, com os comandos de validacao. Uma meta de cobertura de 90% so se aplica se estiver definida para a demanda ou o repositorio; ela nao substitui testes dos comportamentos importantes.
- Falha simulada: o plano promete cobertura acima de 90%, mas nao inclui teste para um criterio de aceite e afirma que os testes passaram sem evidencia.
- Ajuste: ligar cada criterio de aceite a um teste, indicar como sera executado e marcar resultados ainda nao executados como nao verificados.
- Causa principal: erro de raciocinio ao tratar cobertura como prova suficiente e declarar sucesso sem evidencia.

### 2. Scan de seguranca

- Entrada: demanda para um agente consumir conteudo externo, com restricoes de ferramentas e permissoes.
- Resultado correto: o plano trata o conteudo externo como dado nao confiavel, preserva as instrucoes autorizadas e inclui revisao e verificacoes de seguranca adequadas ao risco.
- Falha simulada: o plano permite que instrucoes encontradas no conteudo externo autorizem comandos ou acesso a recursos, e considera um scan limpo como garantia contra prompt injection.
- Ajuste: separar dados de instrucoes, limitar ferramentas e permissoes e incluir casos adversariais de prompt injection na avaliacao. Scans ajudam a detectar problemas, mas nao provam ausencia de vulnerabilidades.
- Causa principal: erro de raciocinio ao confiar no conteudo externo e superestimar o scan.

### 3. Lint

- Entrada: demanda de refatoracao, com configuracao de lint e comandos definidos no repositorio.
- Resultado correto: o plano usa o lint e a formatacao do projeto, limita as mudancas ao escopo e registra como verificar o resultado.
- Falha simulada: o plano inventa um comando de lint e propoe reformatar arquivos nao relacionados, seguindo um padrao diferente do configurado.
- Ajuste: consultar os scripts e configuracoes atuais, escolher o comando correto e restringir a formatacao aos arquivos da tarefa.
- Causa principal: uso incorreto de ferramenta e contexto insuficiente sobre as convencoes do projeto.

### 4. Congruencia com a especificacao

- Entrada: issue atualizada com criterios de aceite e restricoes, junto de um plano antigo e do SHA atual do repositorio.
- Resultado correto: o plano cobre os criterios atuais, identifica os componentes afetados e respeita o escopo e as restricoes.
- Falha simulada: o agente usa o plano antigo, deixa um requisito novo de fora e propoe mudancas fora do objetivo da demanda.
- Ajuste: retomar a fonte de verdade atual, comparar cada etapa com os criterios de aceite e atualizar o plano antes da implementacao.
- Causa principal: contexto desatualizado, gerando drift no planejamento.

### 5. Secret scanning

- Entrada: demanda de integracao que exige autenticacao, com politica de secrets e limites de acesso do repositorio, sem fornecer credenciais reais ao agente.
- Resultado correto: o plano referencia o mecanismo autorizado de secrets, usa menor privilegio e inclui verificacao para evitar exposicao de tokens, senhas ou credenciais no codigo e nos logs.
- Falha simulada: o plano propoe uma senha hardcoded ou registrar o token nos logs para depuracao.
- Ajuste: retirar essa proposta, usar o mecanismo autorizado e incluir secret scanning e revisao. Se uma credencial real ja foi exposta, escalar e priorizar sua revogacao ou rotacao pelo responsavel; apagar o texto nao invalida a credencial, e eventual limpeza do historico exige coordenacao.
- Causa principal: erro de raciocinio sobre armazenamento e exposicao de credenciais.

### Reflexaoo

Qualidade, seguranca e consistencia devem ser medidas pelos criterios definidos na demanda: cobertura dos requisitos pelo plano, escopo respeitado, validacoes verificaveis, contexto atual e riscos tratados. Os quality gates estabelecidos no repositorio aplicam as regras obrigatorias de aceitacao. Depois de corrigir o plano, e preciso avaliar novamente os mesmos casos.

Devem bloquear a entrega: requisito obrigatorio ignorado, exposicao de credenciais, acao perigosa sem aprovacao e resultado de validacao inventado ou evidencia obrigatoria ausente. Falhas transitorias podem ter retries limitados; falhas de seguranca ou permissao exigem parada e escalacao imediata, sem esperar esgotar retries.

Fontes oficiais: [sinais de avaliacao e quality gates](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/5-evaluation-signals-quality-gates), [analise de falhas e ajuste](https://learn.microsoft.com/en-us/training/modules/memory-state-evaluation/6-agent-failures-behavior-improvement) e [tratamento de dados sensiveis expostos](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository).
