# Curso - Módulo 1: Fundamentos da IA agêntica no GitHub

Fonte: [Fundamentos da IA Agêntica no GitHub](https://learn.microsoft.com/pt-br/training/modules/foundations-agentic-ai/)

Cobertura da prova: introdução transversal, com ênfase no **Domínio 1: preparar a arquitetura do agente e os processos do SDLC**.

O módulo reúne oito unidades sobre como agentes de codificação planejam, executam e avaliam trabalhos dentro dos fluxos do GitHub.

## Resumo

### O que é IA agêntica

Um agente de IA recebe um objetivo e usa um modelo, instruções, contexto e ferramentas para alcançá-lo. Um assistente normalmente responde a perguntas ou apresenta sugestões. O agente, por sua vez, pode elaborar um plano, executar ações, observar os resultados e ajustar o trabalho ao longo da tarefa.

Essa autonomia precisa de limites. No desenvolvimento de software, o agente deve atuar dentro de um escopo definido, com as permissões mínimas necessárias, pontos de revisão humana e evidências que permitam conferir o que foi feito.

### Agentes ao longo do SDLC

Um agente pode participar de várias etapas do ciclo de vida do software:

- interpretar e decompor requisitos;
- elaborar um plano de implementação;
- alterar código ou configuração;
- executar testes e outras verificações;
- preparar uma pull request;
- analisar feedback e corrigir a solução;
- apoiar a operação e a manutenção do sistema.

A responsabilidade pelo resultado continua sendo humana e organizacional. O agente pode acelerar tarefas, mas não substitui revisão, governança nem decisão técnica.

### Ciclo: planejar, agir e avaliar

O trabalho do agente segue um ciclo:

1. **Planejar:** compreender o objetivo, o contexto, as restrições e os critérios de sucesso.
2. **Agir:** usar ferramentas para pesquisar, editar, testar ou registrar o resultado.
3. **Avaliar:** conferir as evidências, a qualidade, a segurança e a aderência ao objetivo.
4. **Repetir ou encerrar:** corrigir o plano quando necessário ou concluir a tarefa com um resultado pronto para revisão.

Esse ciclo transforma uma conversa em um processo que pode ser acompanhado. Cada etapa deve deixar registros suficientes para explicar o que foi tentado, qual foi o resultado e por que determinada decisão foi tomada.

### GitHub como sistema de registro e plano de controle

O GitHub reúne os artefatos e controles que tornam o trabalho do agente rastreável:

- issues e discussions registram o objetivo e o contexto;
- branches isolam as alterações;
- commits registram mudanças concretas;
- pull requests concentram revisão e feedback;
- GitHub Actions executa verificações automatizadas;
- rulesets, CODEOWNERS e proteção de branch estabelecem limites;
- logs e artefatos ajudam a reconstruir a execução.

O agente trabalha dentro desse fluxo. O GitHub continua sendo a fonte de verdade para saber o que foi solicitado, alterado, testado e aprovado.

### Riscos e antipadrões

Os principais riscos são:

- aceitar uma alteração sem verificar o resultado;
- conceder mais permissões do que a tarefa exige;
- usar contexto incompleto ou desatualizado;
- executar comandos destrutivos sem aprovação;
- perder o histórico de decisões e evidências;
- confundir uma resposta plausível com uma resposta correta.

Também é um problema deixar o agente trabalhar sem critérios de sucesso, permitir mudanças fora do escopo, ignorar testes ou não definir um ponto de revisão humana.

### O agente como colaborador

O trabalho gerado pelo agente deve ser tratado como qualquer outra contribuição ao repositório: precisa de contexto, evidências e revisão. A pessoa responsável deve:

- fornecer um objetivo claro e o contexto necessário;
- analisar o plano e as alterações;
- executar ou revisar as verificações;
- confirmar a segurança e a aderência ao escopo;
- aprovar, solicitar ajustes ou rejeitar o resultado.

Uma boa colaboração depende de ciclos curtos de feedback e de resultados verificáveis, não da aceitação automática da primeira resposta.

## Checklist de aprendizado

- [x] Consigo diferenciar um agente de um assistente.
- [x] Consigo explicar o ciclo de planejar, agir e avaliar.
- [x] Consigo descrever o GitHub como sistema de registro e plano de controle.
- [x] Sei apontar pelo menos três riscos de uma autonomia sem supervisão.
- [x] Sei identificar as evidências necessárias antes de aprovar o trabalho de um agente.

## Perguntas de revisão

1. Em que ponto do SDLC um agente pode gerar mais valor no seu projeto?
2. De quais ferramentas ele precisa e quais acessos devem ser somente leitura?
3. Quais evidências mostram que uma alteração está pronta para revisão?
4. Quais ações devem exigir aprovação humana?
5. Como reconstruir o que o agente fez depois de uma falha?

## Respostas

1. O agente pode contribuir em várias etapas: definição de requisitos, planejamento, implementação, validação e revisão. O valor gerado depende de um ambiente bem configurado, com escopo, permissões e critérios de aceite claros.

2. O agente pode precisar ler o repositório, criar uma branch de trabalho, alterar arquivos dentro do escopo e executar testes. Alterações em branches protegidas, acesso a secrets, merges e deploys em produção devem permanecer bloqueados ou exigir aprovação.

3. As principais evidências são um plano claro, commits organizados, testes aprovados, verificações de qualidade e segurança concluídas e uma pull request que explique as alterações realizadas.

4. Deploys em ambientes críticos, merges em branches protegidas, exclusão de repositórios ou recursos e mudanças com impacto direto em produção devem exigir aprovação humana.

5. Eu começaria pelo objetivo e pelo plano original. Depois, revisaria os commits, as ações executadas, os logs, os testes e as demais evidências para localizar a origem da falha e propor uma correção.

## Relação com o GH-600

O módulo apresenta a base para os temas seguintes: arquitetura do agente, ferramentas, memória e estado, avaliação, coordenação multiagente e guardrails.
