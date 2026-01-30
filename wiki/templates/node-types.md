# Node Types Reference

## Triggers

| Type | Name | Description |
|------|------|-------------|
| `trigger_manual` | Manual | Button press trigger |
| `trigger_schedule` | Schedule | Cron-based schedule |
| `trigger_file_watch` | File Watch | File system changes |
| `trigger_webhook` | Webhook | HTTP receiver |
| `trigger_startup` | Startup | App launch trigger |
| `trigger_clipboard` | Clipboard | Clipboard changes |
| `trigger_hotkey` | Hotkey | Keyboard shortcut |

## Actions

| Type | Name | Description |
|------|------|-------------|
| `action_notification` | Notification | Desktop notification |
| `action_file` | File | Read/write/append files |
| `action_file_manage` | File Manage | Copy/move/delete |
| `action_file_list` | List Files | Directory listing |
| `action_http` | HTTP Request | API calls |
| `action_script` | Shell Command | Run commands |
| `action_log` | Log | Log messages |
| `action_date` | Date/Time | Date operations |
| `action_delay` | Delay | Wait/sleep |

## Conditions

| Type | Name | Ports |
|------|------|-------|
| `condition_if` | If/Else | `true`, `false` |
| `condition_switch` | Switch | `case1`, `case2`, `default` |
| `condition_filter` | Filter | `match`, `nomatch` |
| `condition_is_empty` | Is Empty | `true`, `false` |
| `condition_type_check` | Type Check | `true`, `false` |

## Loops

| Type | Name | Ports |
|------|------|-------|
| `loop_foreach` | For Each | `loop`, `done` |
| `loop_repeat` | Repeat | `loop`, `done` |
| `loop_while` | While | `loop`, `done` |

## AI

| Type | Name | Description |
|------|------|-------------|
| `action_ai` | AI Prompt | LLM integration |

## Utilities

| Type | Name | Description |
|------|------|-------------|
| `utility_json_parse` | JSON Parse | Parse JSON string |
| `utility_json_stringify` | JSON Stringify | Convert to JSON |
| `utility_delay` | Delay | Wait milliseconds |
| `action_csv_parse` | CSV Parse | Parse CSV data |
| `action_zip_compress` | Compress | Create ZIP archive |
| `action_zip_extract` | Extract | Extract ZIP archive |
