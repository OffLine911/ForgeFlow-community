# Custom Node Builder Overview

Create your own nodes without coding using the visual Custom Node Builder.

## What are Custom Nodes?

Custom nodes are user-defined automation blocks that can:

- Run **shell commands** (PowerShell, Bash, Python)
- Make **HTTP requests** to any API
- Execute **JavaScript** code

## Opening the Builder

1. Look at the **sidebar** on the left
2. Scroll to **"Custom Nodes"** section
3. Click the **+** button

## Creating a Node

### Step 1: Basic Info

| Field | Description |
|-------|-------------|
| Icon | Choose an emoji |
| Name | Display name |
| Category | Action or Utility |
| Description | What it does |

### Step 2: Action Type

Choose one:
- 🖥️ **Shell Command** - Run terminal commands
- 🌐 **HTTP Request** - Make API calls
- 📜 **JavaScript** - Run custom code

### Step 3: Input Fields

Define configurable inputs (see [Input Fields](input-fields.md))

### Step 4: Configure Action

Set up command/URL/script with `{{variable}}` placeholders

## Managing Nodes

| Action | How |
|--------|-----|
| Edit | Hover node → Click ⚙️ |
| Delete | Hover node → Click 🗑️ |
| Use | Drag or click to add |

## Next Steps

- [Shell Commands](shell-commands.md)
- [HTTP Requests](http-requests.md)
- [JavaScript](javascript.md)
- [Input Fields](input-fields.md)
