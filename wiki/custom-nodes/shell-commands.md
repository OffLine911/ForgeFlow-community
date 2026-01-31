# Shell Command Nodes

Run terminal commands, scripts, and system operations.

## Configuration

| Field | Description |
|-------|-------------|
| Command | Executable name or path |
| Arguments | Command line arguments |
| Working Directory | Where to run (optional) |

## Variable Placeholders

Use `{{field_name}}` to insert input values:

```
python {{script_path}} --input {{input_file}}
```

## Examples

### Run Python Script

**Command:** `python`  
**Arguments:** `{{script_path}} --input {{input_file}}`  
**Working Dir:** `{{folder}}`

**Input Fields:**
- `script_path` (File Picker)
- `input_file` (File Picker)
- `folder` (Folder Picker)

---

### Convert with FFmpeg

**Command:** `ffmpeg`  
**Arguments:** `-i {{input}} -vf scale={{width}}:{{height}} {{output}}`

**Input Fields:**
- `input` (File Picker)
- `output` (Text)
- `width` (Number)
- `height` (Number)

---

### Git Commit

**Command:** `git`  
**Arguments:** `commit -m "{{message}}"`  
**Working Dir:** `{{repo_path}}`

**Input Fields:**
- `message` (Text)
- `repo_path` (Folder Picker)

---

### PowerShell Script

**Command:** `powershell`  
**Arguments:** `-ExecutionPolicy Bypass -File {{script}}`

**Input Fields:**
- `script` (File Picker)

---

### Node.js Script

**Command:** `node`  
**Arguments:** `{{script}} {{args}}`

**Input Fields:**
- `script` (File Picker)
- `args` (Text)

## Output

Shell commands return:

```json
{
  "stdout": "command output",
  "stderr": "error output",
  "exitCode": 0,
  "success": true
}
```

## Tips

- Use full paths if command not in PATH
- Quote paths with spaces: `"{{path}}"`
- Check exit codes for error handling
