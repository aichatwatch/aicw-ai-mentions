---
title: MCP server
description: Start the MCP server so Claude, Codex, ChatGPT, or another MCP client can run scans and read reports.
---

MCP (Model Context Protocol) is a standard way for an AI agent to call tools. AICW AI Mentions can run as an MCP server. An agent can then start scans, list saved scans, and rebuild reports.

## Start the server over stdio

Stdio is the default mode. The MCP client starts the server as a child process. Use it for desktop agents. Run this command to test it.

```sh
npx -y aicw-ai-mentions@latest mcp
```

`mcp-server` is another name for the `mcp` command.

## Add the server to a client

### Claude Code

Run this command. It adds the server to Claude Code.

```sh
claude mcp add --transport stdio aicw-ai-mentions -- npx -y aicw-ai-mentions@latest mcp
```

### Claude Desktop and other stdio clients

Add this to the MCP settings of the client.

```json
{
  "mcpServers": {
    "aicw-ai-mentions": {
      "command": "npx",
      "args": ["-y", "aicw-ai-mentions@latest", "mcp"]
    }
  }
}
```

### Codex

Add this to the Codex configuration file. The `env_vars` line passes your API keys to the server.

```toml
[mcp_servers.aicw-ai-mentions]
command = "npx"
args = ["-y", "aicw-ai-mentions@latest", "mcp"]
env_vars = ["OPENROUTER_API_KEY", "OPENAI_API_KEY", "ANTHROPIC_API_KEY", "PERPLEXITY_API_KEY"]
```

## Start the server over HTTP

Some clients, such as ChatGPT, need an HTTPS address. For this, start the HTTP server.

```sh
aicw-ai-mentions mcp --http --port 8787
```

Then expose the port with a tunnel or a deployment. ChatGPT needs an HTTPS Streamable HTTP address that ends in `/mcp`. Add it in ChatGPT under Settings, then Apps & Connectors.

| Flag | Meaning | Default |
| --- | --- | --- |
| `--http` | Use the HTTP transport. | stdio |
| `--stdio` | Use the stdio transport. | on |
| `--port` | The port to listen on. | `8787` |
| `--host` | The address to listen on. | `127.0.0.1` |
| `--path` | The URL path of the MCP endpoint. | `/mcp` |

You can also write `--transport http` or `--transport stdio`.

<Warning>
The HTTP server has no login. Anyone who can reach it can run scans with your API keys. It can also store an OpenRouter key in your local credentials file. Expose it only through a tunnel or deployment that you trust. Use stdio for desktop agents.
</Warning>

## The tools

The server has seven tools.

| Tool | What it does |
| --- | --- |
| `aicw_openrouter_key_status` | Tells you if an OpenRouter key is set in the environment or in the encrypted file. It does not show the key. |
| `aicw_set_openrouter_api_key` | Stores an OpenRouter key in the encrypted local credentials file. |
| `aicw_data_location` | Shows the data folder, the projects folder, and the reports folder. |
| `aicw_list_projects` | Lists saved scans and their report data. |
| `aicw_get_project` | Reads the questions and the report data of one saved scan. |
| `aicw_scan` | Creates and runs a new scan. |
| `aicw_rebuild_report` | Builds a report again from saved data. It does not call any AI model. |

### aicw_scan options

| Option | Meaning |
| --- | --- |
| `subject` | The company, product, person, topic, or market to scan. Required. |
| `questions` | The number of template questions to run. A whole number from 1 to 20. |
| `templateText` | A line-based question template. Use `{{SUBJECT}}` for the subject. |
| `templatePath` | The path of a Markdown template file that the server can read. |
| `timeoutSeconds` | The longest wait for the scan. Default 1800. Maximum 7200. |

A full scan can take several minutes. Increase the tool timeout in your MCP client. To replace the default questions, pass `templateText`.

```json
{
  "subject": "Y Combinator",
  "templateText": "Which sources cite {{SUBJECT}} most often?\nWhich competitors or alternatives are mentioned near {{SUBJECT}}?",
  "questions": 2
}
```

### Other tool options

- `aicw_list_projects` takes an optional `filter` (part of a name) and `limit` (1 to 200, default 50).
- `aicw_get_project` takes `project`, the name of a saved scan.
- `aicw_rebuild_report` takes `project`, an optional `date` in `YYYY-MM-DD` format, and `timeoutSeconds` (default 600).
- `aicw_set_openrouter_api_key` takes `apiKey` and an optional `overwrite` (default true).

## Add the agent skill

The package also has a skill that tells an agent how to use these tools. See [Agent skill](/agent-skill).
