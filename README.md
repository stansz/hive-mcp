# hive-mcp

MCP server for [Agent Hive](https://github.com/stansz/agent-hive) — connect any MCP-compatible client (Claude Code, Cursor, OpenClaw, etc.) to your self-hosted coding agent.

## Quick Start

```bash
export HIVE_URL=https://your-hive.example.com
export HIVE_TOKEN=your-api-token

npx github:stansz/hive-mcp
```

Not published to npm — run directly from GitHub. Requires Node >= 18.

## Tools

| Tool | Description |
|------|-------------|
| `hive_prompt` | Start a coding task. Optionally clone a repo, set model/provider, run review cycles. |
| `hive_status` | Check session state, message count, model, streaming status. |
| `hive_abort` | Cancel a running session by ID. |
| `hive_guide` | Get available providers, features, and preset prompt templates. |

## Configuration

### Env Vars

| Var | Required | Description |
|-----|----------|-------------|
| `HIVE_URL` | Yes | Base URL of your Agent Hive instance |
| `HIVE_TOKEN` | Yes | API bearer token (must match the VPS `.env` API_TOKEN) |

### Claude Code (`.claude/settings.json`)
```json
{
  "mcpServers": {
    "agent-hive": {
      "command": "npx",
      "args": ["github:stansz/hive-mcp"],
      "env": {
        "HIVE_URL": "https://your-hive.example.com",
        "HIVE_TOKEN": "your-api-token"
      }
    }
  }
}
```

### Cursor (`.cursor/mcp.json`)
```json
{
  "mcpServers": {
    "agent-hive": {
      "command": "npx",
      "args": ["github:stansz/hive-mcp"],
      "env": {
        "HIVE_URL": "https://your-hive.example.com",
        "HIVE_TOKEN": "your-api-token"
      }
    }
  }
}
```

### OpenClaw (`openclaw.json`)
```json
{
  "mcp": {
    "servers": {
      "agent-hive": {
        "command": "npx",
        "args": ["github:stansz/hive-mcp"],
        "env": {
          "HIVE_URL": "https://your-hive.example.com",
          "HIVE_TOKEN": "your-api-token"
        }
      }
    }
  }
}
```

## Example

```bash
# Start a task
export HIVE_URL=https://your-hive.example.com
export HIVE_TOKEN=your-token
npx github:stansz/hive-mcp <<< '{"tool":"hive_prompt","args":{"prompt":"Write a hello world in Python"}}'

# Check status (replace sessionId with actual)
npx github:stansz/hive-mcp <<< '{"tool":"hive_status","args":{"sessionId":"abc-123"}}'
```

## License

BSD 3-Clause
