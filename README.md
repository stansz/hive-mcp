# hive-mcp

MCP server for [Agent Hive](https://github.com/stansz/agent-hive) — connect any MCP-compatible client (Claude Code, Cursor, OpenClaw, etc.) to your Hive coding agent.

## Setup

```bash
# Configure env vars
export HIVE_URL=https://your-hive-instance.com
export HIVE_TOKEN=your-api-token

# Run
npx @oatclaw/hive-mcp
```

## Tools

| Tool | Description |
|------|-------------|
| `hive_prompt` | Start a coding task on the Hive VPS |
| `hive_status` | Check status of a running/completed session |
| `hive_abort` | Cancel a running session |
| `hive_snippet` | Quick code task without a repo — send code + prompt, get result |
| `hive_result` | Get the full output of a completed session |

## Configuration

### Claude Code (`.claude/settings.json`)
```json
{
  "mcpServers": {
    "agent-hive": {
      "command": "npx",
      "args": ["@oatclaw/hive-mcp"],
      "env": {
        "HIVE_URL": "https://hive.ogsapps.cc",
        "HIVE_TOKEN": "your-token"
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
      "args": ["@oatclaw/hive-mcp"],
      "env": {
        "HIVE_URL": "https://hive.ogsapps.cc",
        "HIVE_TOKEN": "your-token"
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
        "args": ["@oatclaw/hive-mcp"],
        "env": {
          "HIVE_URL": "https://hive.ogsapps.cc",
          "HIVE_TOKEN": "your-token"
        }
      }
    }
  }
}
```

## Env Vars

| Var | Required | Description |
|-----|----------|-------------|
| `HIVE_URL` | Yes | Base URL of your Agent Hive instance |
| `HIVE_TOKEN` | Yes | API bearer token |

## License

BSD-3-Clause
