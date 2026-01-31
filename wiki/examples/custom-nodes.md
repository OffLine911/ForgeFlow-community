# Custom Node Examples

Ready-to-use custom node configurations.

---

## 💬 Send Discord Message

**Action:** HTTP Request

| Setting | Value |
|---------|-------|
| Method | POST |
| URL | `{{webhook_url}}` |
| Headers | `{"Content-Type": "application/json"}` |
| Body | `{"content": "{{message}}", "username": "{{bot_name}}"}` |

**Input Fields:**
| Variable | Label | Type |
|----------|-------|------|
| `webhook_url` | Webhook URL | Password |
| `message` | Message | Textarea |
| `bot_name` | Bot Name | Text |

---

## 📱 Send Slack Message

**Action:** HTTP Request

| Setting | Value |
|---------|-------|
| Method | POST |
| URL | `https://hooks.slack.com/services/{{webhook_id}}` |
| Headers | `{"Content-Type": "application/json"}` |
| Body | `{"text": "{{message}}", "channel": "{{channel}}"}` |

**Input Fields:**
| Variable | Label | Type |
|----------|-------|------|
| `webhook_id` | Webhook ID | Password |
| `message` | Message | Textarea |
| `channel` | Channel | Text |

---

## 🐍 Run Python Script

**Action:** Shell Command

| Setting | Value |
|---------|-------|
| Command | `python` |
| Arguments | `{{script}} {{args}}` |
| Working Dir | `{{folder}}` |

**Input Fields:**
| Variable | Label | Type |
|----------|-------|------|
| `script` | Python Script | File Picker |
| `args` | Arguments | Text |
| `folder` | Working Directory | Folder Picker |

---

## 🖼️ Resize Image (FFmpeg)

**Action:** Shell Command

| Setting | Value |
|---------|-------|
| Command | `ffmpeg` |
| Arguments | `-i {{input}} -vf scale={{width}}:{{height}} {{output}}` |

**Input Fields:**
| Variable | Label | Type |
|----------|-------|------|
| `input` | Input Image | File Picker |
| `output` | Output Path | Text |
| `width` | Width | Number |
| `height` | Height | Number |

---

## 📊 CSV to JSON

**Action:** JavaScript

```javascript
const csv = input._previousOutput;
const lines = csv.trim().split('\n');
const headers = lines[0].split(',').map(h => h.trim());

const result = lines.slice(1).map(line => {
  const values = line.split(',');
  const obj = {};
  headers.forEach((h, i) => {
    obj[h] = values[i]?.trim() || '';
  });
  return obj;
});

return result;
```

**Input Fields:** None (uses previous output)

---

## 🔢 Calculate Statistics

**Action:** JavaScript

```javascript
const numbers = input._previousOutput;

if (!Array.isArray(numbers)) {
  return { error: 'Input must be an array' };
}

const sum = numbers.reduce((a, b) => a + b, 0);
const avg = sum / numbers.length;
const sorted = [...numbers].sort((a, b) => a - b);
const median = sorted[Math.floor(sorted.length / 2)];

return {
  count: numbers.length,
  sum: sum,
  average: avg,
  min: Math.min(...numbers),
  max: Math.max(...numbers),
  median: median
};
```

---

## 🔍 Extract URLs

**Action:** JavaScript

```javascript
const text = input._previousOutput;
const urlRegex = /https?:\/\/[^\s<>"{}|\\^`\[\]]+/g;
const urls = text.match(urlRegex) || [];

return {
  urls: urls,
  count: urls.length,
  unique: [...new Set(urls)]
};
```

---

## 📧 Send Email (via API)

**Action:** HTTP Request

| Setting | Value |
|---------|-------|
| Method | POST |
| URL | `https://api.sendgrid.com/v3/mail/send` |
| Headers | `{"Authorization": "Bearer {{api_key}}", "Content-Type": "application/json"}` |
| Body | See below |

**Body:**
```json
{
  "personalizations": [{"to": [{"email": "{{to_email}}"}]}],
  "from": {"email": "{{from_email}}"},
  "subject": "{{subject}}",
  "content": [{"type": "text/plain", "value": "{{message}}"}]
}
```

**Input Fields:**
| Variable | Label | Type |
|----------|-------|------|
| `api_key` | SendGrid API Key | Password |
| `to_email` | To Email | Text |
| `from_email` | From Email | Text |
| `subject` | Subject | Text |
| `message` | Message | Textarea |

---

## 🗄️ Git Commit & Push

**Action:** Shell Command

| Setting | Value |
|---------|-------|
| Command | `powershell` |
| Arguments | `-Command "cd '{{repo}}'; git add .; git commit -m '{{message}}'; git push"` |

**Input Fields:**
| Variable | Label | Type |
|----------|-------|------|
| `repo` | Repository Path | Folder Picker |
| `message` | Commit Message | Text |
