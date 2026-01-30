# Connections & Ports

Connections link nodes together in a workflow.

## Connection Structure

```json
{
  "sourceIndex": 0,
  "sourcePort": "out",
  "targetIndex": 1,
  "targetPort": "in"
}
```

## Fields

| Field | Description |
|-------|-------------|
| `sourceIndex` | Index of source node in `nodes` array |
| `sourcePort` | Output handle ID |
| `targetIndex` | Index of target node in `nodes` array |
| `targetPort` | Input handle ID |

## Standard Ports

Most nodes use:
- **Input:** `"in"`
- **Output:** `"out"`

## Special Output Ports

### Condition Nodes

| Port | When Used |
|------|-----------|
| `"true"` | Condition is true |
| `"false"` | Condition is false |

### Loop Nodes

| Port | When Used |
|------|-----------|
| `"loop"` | Each iteration |
| `"done"` | After loop completes |

### Filter Nodes

| Port | When Used |
|------|-----------|
| `"match"` | Items that match |
| `"nomatch"` | Items that don't match |

### Switch Nodes

| Port | When Used |
|------|-----------|
| `"case1"` | First case matches |
| `"case2"` | Second case matches |
| `"default"` | No case matches |

## Example

```json
{
  "nodes": [
    { "type": "trigger_manual", ... },
    { "type": "condition_if", ... },
    { "type": "action_notification", ... },
    { "type": "action_log", ... }
  ],
  "connections": [
    { "sourceIndex": 0, "sourcePort": "out", "targetIndex": 1, "targetPort": "in" },
    { "sourceIndex": 1, "sourcePort": "true", "targetIndex": 2, "targetPort": "in" },
    { "sourceIndex": 1, "sourcePort": "false", "targetIndex": 3, "targetPort": "in" }
  ]
}
```
