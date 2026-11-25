# Workflow

Plugin independente de Isaac para planejar, executar e verificar entregas em português do Brasil. Serve para desenvolvimento de software, jogos e outros projetos técnicos. Inclui um [fluxo de trabalho](skills/workflow/SKILL.md), um [roteiro de jogos](skills/workflow/references/jogos.md) e um [agente de revisão](agents/delivery-reviewer.md) para o Claude Code.

Abra uma conversa e descreva a tarefa normalmente. O fluxo começa decidindo o que fazer e como verificar o resultado. O pacote inclui skills do Superpowers e agentes do ECC. Alethe pode complementar a delegação quando estiver disponível.

## Modo Foco

Diga `modo foco` para receber atualizações e respostas finais em até três linhas na conversa. Diga `detalhar` para expandir uma resposta ou `sair do modo foco` para voltar ao formato padrão.

## Revisão cruzada local

O comando reúne 12 papéis executores e 12 críticos. Cada crítico avalia as 12 contribuições, incluindo a do seu par, com evidência e sugestão. Contribuições com pedidos de correção voltam para seus responsáveis. O relatório JSON registra as rodadas e indica aprovação pelos críticos, impasse ou interrupção.

Use Node.js 20+ e inicie três instâncias locais de `llama-server` com seus pesos GGUF. Os exemplos usam nomes de arquivo ilustrativos.

```text
llama-server -m planejamento.gguf --host 127.0.0.1 --port 8080 -c 16384
llama-server -m codigo.gguf --host 127.0.0.1 --port 8081 -c 16384
llama-server -m critica.gguf --host 127.0.0.1 --port 8082 -c 16384
node scripts/revisao-local.mjs pedido.txt relatorio.json 3
```

Use um caminho de relatório novo a cada execução. Inclua objetivo, critérios de aceitação e evidências de verificação no pedido. A inferência usa a máquina local. As três instâncias precisam caber juntas na memória disponível.

O comando gera e revisa propostas em texto. Para validar scripts, importações ou renders, execute os checks no projeto e forneça os resultados como evidência. A revisão visual desta versão usa evidências textuais.

## Agentes incluídos

No Claude Code, o pacote disponibiliza o agente próprio de revisão de entregas e [oito agentes do ECC 2.2.3](third-party/ecc/README.md). Eles são carregados diretamente pelo Workflow.

## Skills incluídas

O Workflow incorpora [12 skills do Superpowers 7.0.2](third-party/superpowers/README.md), incluindo brainstorming, planejamento, depuração e verificação. As referências internas usam o namespace do Workflow.

## Biblioteca sob demanda

O [índice do ECC](library/ecc/CATALOG.md) referencia 314 skills incluídas na pasta library. Elas ficam disponíveis para leitura seletiva em clientes com acesso aos arquivos do plugin. O Workflow abre as instruções pertinentes à tarefa e delega quando a divisão de trabalho justificar o custo. Skills locais de outras origens e integrações podem ser usadas quando o cliente já as disponibiliza.

## Ferramentas sob demanda

O pacote inclui [Watch, Context Mode, RTK e Headroom](library/tools/README.md). Os executáveis distribuídos de RTK e Headroom têm alvo Windows x64. A integração reaproveita os servidores já configurados no cliente ou permite apontar para os componentes incluídos. Os servidores MCP são iniciados quando configurados pelo usuário.

## Instalação pelo GitHub

Depois de publicar o repositório, substitua `SEU_USUARIO` pelo seu usuário.

### Claude Code

```text
/plugin marketplace add SEU_USUARIO/workflow
/plugin install workflow@workflow --scope user
/reload-plugins
```

Ao abrir, retomar ou limpar uma sessão, o hook de inicialização exibe **Workflow 1.5.0 ativo. Ainda está em desenvolvimento, então podem ocorrer falhas. Vamos corrigi-las ao longo do desenvolvimento.** quando o Claude Code executa o evento. O aviso usa Node.js e independe de enviar uma tarefa. Para invocação manual, use `/workflow:workflow`.

### Codex

```sh
codex plugin marketplace add SEU_USUARIO/workflow
codex plugin add workflow@workflow
```

Para instalar de um clone local, passe o caminho da pasta ao comando de adicionar marketplace.

## Licença

O conteúdo original do Workflow é distribuído sob a [licença MIT](LICENSE). Os componentes do [ECC](third-party/ecc/README.md) e do [Superpowers](third-party/superpowers/README.md) mantêm suas licenças e créditos.
