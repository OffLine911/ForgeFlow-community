# Contributing to ForgeFlow Community Templates

Thanks for contributing! Here's how to add your workflow templates.

## Quick Start

1. **Fork** this repository
2. **Edit** `templates.json` and add your template
3. **Test** your template in ForgeFlow
4. **Submit** a Pull Request

## Template Structure

```json
{
  "id": "my-awesome-workflow",
  "name": "My Awesome Workflow",
  "description": "Brief description of what this workflow does",
  "icon": "🚀",
  "category": "Automation",
  "author": "YourGitHubUsername",
  "nodes": [
    {
      "type": "trigger_manual",
      "position": { "x": 100, "y": 100 },
      "data": {}
    }
  ],
  "connections": [
    {
      "sourceIndex": 0,
      "sourcePort": "out",
      "targetIndex": 1,
      "targetPort": "in"
    }
  ]
}
```

## Fields

| Field | Required | Description |
|-------|----------|-------------|
| `id` | ✅ | Unique kebab-case identifier |
| `name` | ✅ | Human-readable name |
| `description` | ✅ | What the workflow does (1-2 sentences) |
| `icon` | ✅ | Single emoji |
| `category` | ✅ | One of: Automation, Productivity, DevOps, AI, Data, Integration |
| `author` | ✅ | Your GitHub username |
| `nodes` | ✅ | Array of node objects |
| `connections` | ✅ | Array of connection objects |

## Categories

- **Automation** - File operations, scheduled tasks
- **Productivity** - Reminders, timers, organization
- **DevOps** - Monitoring, deployment, health checks
- **AI** - LLM integrations, chatbots, summarization
- **Data** - Transformations, parsing, exports
- **Integration** - Webhooks, APIs, third-party services

## Guidelines

✅ **Do:**
- Test your template before submitting
- Use descriptive names and descriptions
- Include all required fields
- Use appropriate category

❌ **Don't:**
- Include sensitive data (API keys, passwords)
- Submit broken/untested templates
- Use offensive content

## Testing Your Template

1. Copy your template JSON
2. In ForgeFlow, go to Import/Export
3. Paste and import
4. Run the workflow to verify it works

## Questions?

Open an issue if you need help!
