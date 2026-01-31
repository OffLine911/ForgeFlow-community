# Template Examples

Complete, working template examples.

## Simple: Morning Greeting

```json
{
  "id": "morning-greeting",
  "name": "Morning Greeting",
  "description": "Show a greeting every morning at 8 AM",
  "icon": "🌅",
  "category": "Productivity",
  "author": "OffLine911",
  "nodes": [
    {
      "type": "trigger_schedule",
      "position": { "x": 100, "y": 150 },
      "data": { "cron": "0 8 * * *" }
    },
    {
      "type": "action_notification",
      "position": { "x": 350, "y": 150 },
      "data": {
        "title": "Good Morning! ☀️",
        "message": "Have a great day!"
      }
    }
  ],
  "connections": [
    { "sourceIndex": 0, "sourcePort": "out", "targetIndex": 1, "targetPort": "in" }
  ]
}
```

## Intermediate: File Backup

```json
{
  "id": "weekly-backup",
  "name": "Weekly Backup",
  "description": "Backup folder every Sunday at 2 AM",
  "icon": "💾",
  "category": "Automation",
  "author": "OffLine911",
  "nodes": [
    {
      "type": "trigger_schedule",
      "position": { "x": 100, "y": 150 },
      "data": { "cron": "0 2 * * 0" }
    },
    {
      "type": "action_date",
      "position": { "x": 350, "y": 150 },
      "data": { "operation": "now", "format": "YYYY-MM-DD" }
    },
    {
      "type": "action_zip_compress",
      "position": { "x": 600, "y": 150 },
      "data": {
        "sources": "C:\\ImportantFiles",
        "zipPath": "D:\\Backups\\backup-{{output}}.zip"
      }
    },
    {
      "type": "action_notification",
      "position": { "x": 850, "y": 150 },
      "data": {
        "title": "Backup Complete",
        "message": "Weekly backup created!"
      }
    }
  ],
  "connections": [
    { "sourceIndex": 0, "sourcePort": "out", "targetIndex": 1, "targetPort": "in" },
    { "sourceIndex": 1, "sourcePort": "out", "targetIndex": 2, "targetPort": "in" },
    { "sourceIndex": 2, "sourcePort": "out", "targetIndex": 3, "targetPort": "in" }
  ]
}
```

## Advanced: Conditional API Check

```json
{
  "id": "api-monitor",
  "name": "API Health Monitor",
  "description": "Check API and alert on failure",
  "icon": "🌐",
  "category": "DevOps",
  "author": "OffLine911",
  "nodes": [
    {
      "type": "trigger_schedule",
      "position": { "x": 100, "y": 150 },
      "data": { "cron": "*/5 * * * *" }
    },
    {
      "type": "action_http",
      "position": { "x": 350, "y": 150 },
      "data": {
        "method": "GET",
        "url": "https://api.example.com/health"
      }
    },
    {
      "type": "condition_if",
      "position": { "x": 600, "y": 150 },
      "data": { "condition": "{{output.status}} !== 200" }
    },
    {
      "type": "action_notification",
      "position": { "x": 850, "y": 80 },
      "data": {
        "title": "⚠️ API Alert",
        "message": "Health check failed!"
      }
    },
    {
      "type": "action_log",
      "position": { "x": 850, "y": 220 },
      "data": {
        "message": "API OK",
        "level": "info"
      }
    }
  ],
  "connections": [
    { "sourceIndex": 0, "sourcePort": "out", "targetIndex": 1, "targetPort": "in" },
    { "sourceIndex": 1, "sourcePort": "out", "targetIndex": 2, "targetPort": "in" },
    { "sourceIndex": 2, "sourcePort": "true", "targetIndex": 3, "targetPort": "in" },
    { "sourceIndex": 2, "sourcePort": "false", "targetIndex": 4, "targetPort": "in" }
  ]
}
```

## With Loop: Process Files

```json
{
  "id": "batch-processor",
  "name": "Batch File Processor",
  "description": "Process all files in a folder",
  "icon": "📁",
  "category": "Automation",
  "author": "OffLine911",
  "nodes": [
    {
      "type": "trigger_manual",
      "position": { "x": 100, "y": 150 },
      "data": {}
    },
    {
      "type": "action_file_list",
      "position": { "x": 350, "y": 150 },
      "data": {
        "path": "C:\\Input",
        "pattern": "*.txt",
        "include": "files"
      }
    },
    {
      "type": "loop_foreach",
      "position": { "x": 600, "y": 150 },
      "data": {
        "array": "{{output}}",
        "itemVar": "file"
      }
    },
    {
      "type": "action_log",
      "position": { "x": 850, "y": 100 },
      "data": { "message": "Processing: {{file.name}}" }
    },
    {
      "type": "action_notification",
      "position": { "x": 600, "y": 300 },
      "data": {
        "title": "Done",
        "message": "All files processed!"
      }
    }
  ],
  "connections": [
    { "sourceIndex": 0, "sourcePort": "out", "targetIndex": 1, "targetPort": "in" },
    { "sourceIndex": 1, "sourcePort": "out", "targetIndex": 2, "targetPort": "in" },
    { "sourceIndex": 2, "sourcePort": "loop", "targetIndex": 3, "targetPort": "in" },
    { "sourceIndex": 2, "sourcePort": "done", "targetIndex": 4, "targetPort": "in" }
  ]
}
```
