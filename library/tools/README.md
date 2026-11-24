# Ferramentas sob demanda

Use as ferramentas quando reduzirem o tamanho das saídas ou forem necessárias à tarefa. Em uma conversa comum, o Workflow não inicia servidores MCP nem muda o proxy.

| Componente incluído | Quando usar | Como usar |
| --- | --- | --- |
| [Watch 0.3.2](watch/SKILL.md) | Analisar um vídeo pedido pelo usuário | Leia a skill e execute seus scripts via Python. A análise pode requerer ffmpeg, yt-dlp e um mecanismo de transcrição. |
| [Context Mode 2.1.10](context-mode/LICENSE) | Indexar ou filtrar grandes saídas e pesquisar trechos específicos | Reuse a conexão existente. Para usar o servidor incluído, aponte um cliente MCP stdio para `node <caminho>/context-mode/server.mjs`. Requer Node.js 24.15 ou superior. |
| [RTK 1.2.0](rtk/LICENSE) | Reduzir saídas repetitivas de comandos Git e de desenvolvimento | Use o RTK já disponível ou execute `<caminho>/rtk/rtk.exe` no Windows x64. Para outras plataformas, use a distribuição oficial. |
| [Headroom 0.44.0](headroom/) | Comprimir logs ou dados extensos quando a saída filtrada ainda for grande | Reuse o MCP existente. No Windows x64, instale o wheel incluído com a opção MCP. As dependências Python são resolvidas pelo gerenciador de pacotes. |

## Headroom via MCP

Os exemplos pressupõem que o terminal esteja nesta pasta:

```powershell
$wheel = (Resolve-Path ./headroom/headroom_ai-0.44.0-cp310-abi3-win_amd64.whl).Path
uv tool install --python 3.13 "headroom-ai[mcp] @ $(([Uri]$wheel).AbsoluteUri)"
```

Em outras plataformas:

```sh
uv tool install --python 3.13 "headroom-ai[mcp]==0.44.0"
```

Configure um cliente MCP stdio para executar `headroom mcp serve`. Para uso estritamente local, configure `HEADROOM_OFFLINE=1` no ambiente do servidor. A compressão sob demanda usa o MCP. A compressão do tráfego inteiro requer o proxy e fica fora dessa configuração.

## Créditos e distribuição

- [Watch](https://github.com/bradautomates/claude-video), Bradley Bonanno. [MIT](watch/LICENSE).
- [Context Mode](https://github.com/mksglu/context-mode), Mert Koseoglu. [Elastic License 2.0](context-mode/LICENSE).
- [RTK](https://github.com/rtk-ai/rtk). [Licença da distribuição](rtk/LICENSE) e [licença do engine](rtk/LICENSE-ENGINE).
- [Headroom](https://pypi.org/project/headroom-ai/0.44.0/). O wheel foi remontado a partir do cache do uv, com os arquivos verificados pelos hashes do `RECORD`. A distribuição conserva os avisos de licença internos.
