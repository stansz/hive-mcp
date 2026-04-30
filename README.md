# hive-mcp

MCP server for [Agent Hive](https://github.com/stansz/agent-hive) — connect any MCP-compatible client (Claude Code, Cursor, OpenClaw, etc.) to your self-hosted coding agent.

## Quick Start

```bash
# Make sure Agent Hive is running first (see stansz/agent-hive)
# Then connect via MCP:
export HIVE_URL=http://localhost:8080
export HIVE_TOKEN=your-api-token   # Same token from your Hive .env file

npx github:stansz/hive-mcp
```

The `HIVE_TOKEN` must match the `API_TOKEN` you set in Agent Hive's `.env`. Generate one with `openssl rand -hex 32` if you haven't already.

## Setup Examples

### Claude Code (`.claude/settings.json`)
```json
{
  "mcpServers": {
    "agent-hive": {
      "command": "npx",
      "args": ["github:stansz/hive-mcp"],
      "env": {
        "HIVE_URL": "http://localhost:8080",
        "HIVE_TOKEN": "your-generated-token"
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
        "HIVE_URL": "http://localhost:8080",
        "HIVE_TOKEN": "your-generated-token"
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
          "HIVE_URL": "http://localhost:8080",
          "HIVE_TOKEN": "your-generated-token"
        }
      }
    }
  }
}
```

## Tools

| Tool | Description |
|------|-------------|
| `hive_prompt` | Start a coding task. Optionally clone a repo, set model/provider, run review cycles. |
| `hive_status` | Check session state, message count, model, streaming status. |
| `hive_abort` | Cancel a running session by ID. |
| `hive_guide` | Get available providers, features, and preset prompt templates. |

## Configuration

| Var | Required | Description |
|-----|----------|-------------|
| `HIVE_URL` | Yes | Base URL of your Agent Hive instance (e.g. `http://localhost:8080`) |
| `HIVE_TOKEN` | Yes | API bearer token — must match the `API_TOKEN` in Hive's `.env` |

## Example

```bash
export HIVE_URL=http://localhost:8080
export HIVE_TOKEN=your-token

# Start a task
npx github:stansz/hive-mcp <<< '{"tool":"hive_prompt","args":{"prompt":"Write a hello world in Python"}}'

# Check status (replace sessionId with actual)
npx github:stansz/hive-mcp <<< '{"tool":"hive_status","args":{"sessionId":"abc-123"}}'
```

## License

BSD 3-Clause
