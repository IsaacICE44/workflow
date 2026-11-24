---
name: workflow
description: Fluxo autônomo de Isaac para decidir, planejar, implementar, revisar e verificar entregas em projetos de software, jogos e outros trabalhos técnicos. Use automaticamente ao iniciar ou retomar uma tarefa de projeto.
---

# Workflow

Responda em português do Brasil. Ao retomar o trabalho, recupere a etapa atual na fonte disponível, como código, plano, issue ou artefato. Identifique o resultado esperado e quem vai usá-lo.

## 1. Decida o que fazer e como fazer

Use primeiro a skill incluída `workflow:brainstorming` quando houver decisões de produto, design ou abordagem em aberto. Use `workflow:writing-plans` quando a solução já estiver definida e precisar ser dividida em etapas verificáveis. Para mudanças pequenas ou já bem definidas, aplique somente a análise necessária e preserve o escopo.

As instruções do projeto, o pedido e as permissões da sessão controlam alterações em arquivos, git, delegação e ações externas. Os exemplos das skills incorporadas não autorizam commits, publicação ou mudanças fora do escopo.

Defina o resultado observável antes da execução. Quando houver opções em aberto, compare custo, risco e como verificar cada abordagem. Resolva escolhas reversíveis com uma hipótese explícita. Consulte a pessoa quando faltar uma decisão que afete significativamente o escopo ou o resultado.

Escolha a menor entrega que demonstre o resultado. Defina abordagem, sistemas ou artefatos afetados e verificação. Em um bug, use `workflow:systematic-debugging`, reproduza o problema ou obtenha evidência equivalente e delimite a causa. Em uma mudança pequena, confirme brevemente objetivo, abordagem e check.

## 2. Execute com as práticas do projeto

Leia as instruções e siga os pontos de entrada reais. Reuse os padrões existentes e verifique compatibilidade com consumidores, dados e versões já em uso. Em mudanças de estado, confira entrada, saída e recuperação após falha. Execute os checks pertinentes. Em entregas sem código, confira o artefato no formato e no contexto em que será usado.

## 3. Coordene tarefas independentes

Use delegação nativa quando disponível, autorizada e útil. Dê a cada agente um objetivo, o escopo sob sua responsabilidade, as práticas pertinentes e os checks esperados. Revise as evidências e valide a integração no agente principal.

No Claude Code, escolha os agentes incorporados de acordo com o trabalho:

- `workflow:planner` e `workflow:architect` para plano e decisões de arquitetura.
- `workflow:code-explorer` para mapear o fluxo existente e `workflow:code-reviewer` para revisar alterações.
- `workflow:build-error-resolver` para erros de build em TypeScript e `workflow:tdd-guide` quando TDD fizer parte da tarefa.
- `workflow:performance-optimizer` e `workflow:a11y-architect` para desempenho e acessibilidade.
- `workflow:delivery-reviewer` para revisar a entrega final ou mudanças de gameplay.

Peça que o agente responda em português do Brasil e aplique os critérios do projeto. Use a [relação de agentes e créditos](../../third-party/ecc/README.md) para identificar os componentes do ECC incluídos.

## 4. Verifique a entrega

Use `workflow:verification-before-completion`. Execute o fluxo real, confira estados afetados e reporte as evidências, verificações pendentes e o próximo passo concreto. Para jogos, siga o [roteiro de gameplay](references/jogos.md).

As skills do Superpowers e os agentes selecionados do ECC fazem parte deste pacote. Alethe pode complementar a coordenação quando já estiver disponível.
