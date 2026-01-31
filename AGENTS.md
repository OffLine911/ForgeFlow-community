# ForgeFlow Community Templates

## Overview
Community-contributed JSON workflow templates for [ForgeFlow](https://github.com/OffLine911/ForgeFlow) automation engine.

## Structure
- `templates/` - JSON template files (kebab-case filenames matching template ID)
- `index.json` - Template registry with metadata (id, file, name, description, icon, category, author, downloads)
- `wiki/` - Documentation for node types, connections, and variables

## Template JSON Schema
- Required fields: `id`, `name`, `description`, `icon`, `category`, `nodes`, `connections`
- Do NOT include `author` field in template files (managed in index.json only)
- Node structure: `{ type, position: {x, y}, data: {...} }`
- Connection structure: `{ sourceIndex, sourcePort, targetIndex, targetPort }`

## Conventions
- Template ID: kebab-case, must be unique, filename must match ID
- Categories: Automation, Productivity, DevOps, AI, Data, Integration
- Icon: single emoji or icon name (e.g., "github", "clock", "robot")
- Description: clear and concise, under 100 characters
- Variables in templates: use `{{output.fieldName}}` syntax

## Validation
- Ensure valid JSON (no trailing commas)
- Template ID must match between index.json and template file
- All node types must be valid ForgeFlow nodes (see wiki/templates/node-types.md)
- Connection indices must reference valid node array positions
