# Template Structure

Every template is a JSON object with this structure:

```json
{
  "id": "my-template-id",
  "name": "My Template Name",
  "description": "What this template does",
  "icon": "🚀",
  "category": "Automation",
  "author": "YourGitHubUsername",
  "nodes": [...],
  "connections": [...]
}
```

## Required Fields

| Field | Type | Example | Description |
|-------|------|---------|-------------|
| `id` | string | `"file-backup"` | Unique kebab-case identifier |
| `name` | string | `"File Backup"` | Display name shown to users |
| `description` | string | `"Backup files daily"` | Short description (1-2 sentences) |
| `icon` | string | `"💾"` | Single emoji icon |
| `category` | string | `"Automation"` | Template category |
| `author` | string | `"OffLine911"` | Your GitHub username |
| `nodes` | array | `[...]` | Array of node definitions |
| `connections` | array | `[...]` | Array of edge connections |

## Categories

- **Automation** - File operations, scheduled tasks, scripts
- **Productivity** - Reminders, timers, organization tools
- **DevOps** - Monitoring, deployment, CI/CD
- **AI** - LLM integrations, chatbots, summarization
- **Data** - Parsing, transformations, conversions
- **Integration** - Webhooks, APIs, third-party services

## Node Definition

Each node in the `nodes` array:

```json
{
  "type": "node_type_id",
  "position": { "x": 100, "y": 100 },
  "data": {
    "configKey": "configValue"
  }
}
```

See [Node Types Reference](node-types.md) for available types.

## Connection Definition

See [Connections & Ports](connections.md) for details.
