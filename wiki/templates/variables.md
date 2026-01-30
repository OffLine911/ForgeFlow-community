# Variables & Interpolation

Use `{{variableName}}` syntax to insert dynamic values.

## Available Variables

| Variable | Description |
|----------|-------------|
| `{{output}}` | Previous node's output |
| `{{result}}` | Same as output |
| `{{lastOutput}}` | Same as output |
| `{{response}}` | Same as output |
| `{{node_ID}}` | Specific node's output |
| `{{env.VAR}}` | Environment variable |

## Nested Access

Access nested properties with dots:

```
{{output.data.items[0].name}}
```

## Examples

### In Notifications

```json
{
  "type": "action_notification",
  "data": {
    "title": "Status: {{output.status}}",
    "message": "Found {{output.count}} items"
  }
}
```

### In HTTP Requests

```json
{
  "type": "action_http",
  "data": {
    "url": "https://api.example.com/{{output.id}}",
    "headers": "{\"Authorization\": \"Bearer {{env.API_KEY}}\"}"
  }
}
```

### In File Operations

```json
{
  "type": "action_file",
  "data": {
    "mode": "write",
    "path": "C:\\output\\{{output.filename}}.txt",
    "content": "{{output.data}}"
  }
}
```

## Tips

- Use `{{output}}` for simple values
- Use `{{output.property}}` for objects
- Use `{{output[0]}}` for arrays
- Environment variables require setup in Settings
