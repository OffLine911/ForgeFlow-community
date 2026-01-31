# Input Fields

Define configurable inputs for your custom nodes.

## Adding Fields

1. Click **"Add Field"** in the builder
2. Set variable name (used in `{{name}}`)
3. Set display label (shown to users)
4. Choose field type

## Field Types

| Type | Description | Use For |
|------|-------------|---------|
| Text | Single line input | Names, IDs, short values |
| Textarea | Multi-line input | Messages, scripts, JSON |
| Number | Numeric input | Counts, sizes, ports |
| Password | Hidden input | API keys, tokens, secrets |
| Toggle | Boolean switch | Enable/disable options |
| Dropdown | Select from options | Fixed choices |
| File Picker | Choose a file | Input files, scripts |
| Folder Picker | Choose a folder | Directories, output paths |

## Variable Names

Use lowercase with underscores:

✅ Good:
- `api_key`
- `input_file`
- `max_count`

❌ Bad:
- `API Key` (spaces)
- `inputFile` (camelCase works but inconsistent)

## Using in Actions

Reference fields with `{{field_name}}`:

**Shell:**
```
python {{script_path}} --count {{max_count}}
```

**HTTP URL:**
```
https://api.example.com/{{endpoint}}?key={{api_key}}
```

**HTTP Body:**
```json
{"message": "{{message}}", "count": {{count}}}
```

**JavaScript:**
```javascript
const key = input.api_key;
const count = parseInt(input.max_count);
```

## Dropdown Options

For dropdown fields, define options in the builder:

| Value | Label |
|-------|-------|
| `small` | Small (100px) |
| `medium` | Medium (500px) |
| `large` | Large (1000px) |

## Default Values

Set default values for optional fields to prevent empty values.

## Tips

- Use Password type for sensitive data
- Use File/Folder Picker for paths
- Keep variable names short but clear
- Add helpful placeholder text
