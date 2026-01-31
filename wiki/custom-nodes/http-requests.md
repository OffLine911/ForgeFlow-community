# HTTP Request Nodes

Make API calls to any URL.

## Configuration

| Field | Description |
|-------|-------------|
| Method | GET, POST, PUT, PATCH, DELETE |
| URL | API endpoint |
| Headers | JSON object of headers |
| Body | Request body (for POST/PUT) |

## Variable Placeholders

Use `{{field_name}}` anywhere:

```
https://api.example.com/{{endpoint}}?key={{api_key}}
```

## Examples

### POST to Slack

**Method:** `POST`  
**URL:** `https://hooks.slack.com/services/{{webhook_id}}`  
**Headers:**
```json
{"Content-Type": "application/json"}
```
**Body:**
```json
{"text": "{{message}}"}
```

**Input Fields:**
- `webhook_id` (Password)
- `message` (Textarea)

---

### Send Discord Message

**Method:** `POST`  
**URL:** `{{webhook_url}}`  
**Headers:**
```json
{"Content-Type": "application/json"}
```
**Body:**
```json
{"content": "{{message}}", "username": "{{bot_name}}"}
```

**Input Fields:**
- `webhook_url` (Password)
- `message` (Textarea)
- `bot_name` (Text)

---

### Fetch Weather

**Method:** `GET`  
**URL:** `https://api.weatherapi.com/v1/current.json?key={{api_key}}&q={{city}}`

**Input Fields:**
- `api_key` (Password)
- `city` (Text)

---

### GitHub API

**Method:** `GET`  
**URL:** `https://api.github.com/repos/{{owner}}/{{repo}}`  
**Headers:**
```json
{"Authorization": "token {{token}}", "Accept": "application/vnd.github.v3+json"}
```

**Input Fields:**
- `owner` (Text)
- `repo` (Text)
- `token` (Password)

---

### Create Jira Issue

**Method:** `POST`  
**URL:** `https://{{domain}}.atlassian.net/rest/api/3/issue`  
**Headers:**
```json
{"Authorization": "Basic {{auth}}", "Content-Type": "application/json"}
```
**Body:**
```json
{
  "fields": {
    "project": {"key": "{{project}}"},
    "summary": "{{title}}",
    "issuetype": {"name": "Task"}
  }
}
```

## Output

HTTP requests return:

```json
{
  "status": 200,
  "statusText": "OK",
  "headers": {...},
  "body": "response text",
  "json": {...}
}
```

## Tips

- Use Password field type for API keys
- Headers must be valid JSON
- Access response via `{{output.json.property}}`
