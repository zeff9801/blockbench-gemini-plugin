# Gemini MCP Client (MCP SuperAssistant)

## Overview
Use MCP SuperAssistant to connect Gemini (web or AI Studio) to the Blockbench MCP server. This setup does not require a Gemini API key.

## Prereqs
- Blockbench desktop app with the MCP plugin installed
- MCP server enabled in Blockbench Settings > General
- Node.js available for running `npx`

## Setup
1. Confirm the MCP server endpoint in Blockbench Settings > General. The default is `http://localhost:3000/bb-mcp`.
2. Install the MCP SuperAssistant browser extension (Chrome or Firefox).
3. Create a `config.json` for the MCP SuperAssistant proxy:

```json
{
  "mcpServers": {
    "blockbench": {
      "url": "http://localhost:3000/bb-mcp"
    }
  }
}
```

4. Run the MCP SuperAssistant proxy:

```bash
npx -y @srbhptl39/mcp-superassistant-proxy@latest --config ./config.json --outputTransport sse
```

5. In the MCP SuperAssistant extension, connect to the proxy URL:

```text
http://localhost:3006/sse
```

6. Open Gemini (web or AI Studio) and ask it to list MCP tools, then run a simple tool to confirm it reaches Blockbench.

## Notes
- If you prefer streamable HTTP, start the proxy with `--outputTransport streamableHttp` and connect to `http://localhost:3006/mcp`.
- If the extension shows no tools, verify Blockbench is running and the MCP server endpoint matches the proxy config.
- If the proxy fails to connect, confirm Blockbench granted network permission to the MCP plugin.
