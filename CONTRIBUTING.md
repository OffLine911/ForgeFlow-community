# Contributing to ForgeFlow-Community

Thank you for your interest in contributing to ForgeFlow-Community! This guide will help you submit your workflow templates.

## How to Add a New Template

### 1. Create Your Template File

Create a new JSON file in the `templates/` directory with a kebab-case filename matching your template ID:

```
templates/your-template-name.json
```

### 2. Template Structure

Your template file should follow this structure:

```json
{
  "id": "your-template-name",
  "name": "Your Template Name",
  "description": "Brief description of what your template does",
  "icon": "🚀",
  "category": "Automation",
  "nodes": [
    {
      "type": "trigger_manual",
      "position": { "x": 100, "y": 150 },
      "data": {}
    },
    {
      "type": "action_notification",
      "position": { "x": 350, "y": 150 },
      "data": {
        "title": "Hello!",
        "message": "Template executed successfully"
      }
    }
  ],
  "connections": [
    {
      "sourceIndex": 0,
      "sourcePort": "out",
      "targetIndex": 1,
      "targetPort": "in"
    }
  ]
}
```

**Important:** Do NOT include an `author` field in the template file. This is managed in `index.json`.

### 3. Update index.json

Add your template entry to the `templates` array in `index.json`:

```json
{
  "id": "your-template-name",
  "file": "your-template-name.json",
  "name": "Your Template Name",
  "description": "Brief description of what your template does",
  "icon": "🚀",
  "category": "Automation",
  "author": "YourGitHubUsername",
  "downloads": 0
}
```

## Template Validation Checklist

Before submitting your PR, ensure:

- [ ] Template ID is unique and uses kebab-case
- [ ] Filename matches the template ID
- [ ] JSON is valid (no trailing commas, proper syntax)
- [ ] Template ID matches between `index.json` and template file
- [ ] Category is one of: Automation, Productivity, DevOps, AI, Data, Integration
- [ ] Description is clear and concise (under 100 characters)
- [ ] Icon is a single emoji
- [ ] No `author` field in the template file (only in `index.json`)
- [ ] All node types are valid ForgeFlow nodes
- [ ] Connections reference correct node indices
- [ ] Template has been tested in ForgeFlow

## Available Node Types

For a complete list of available node types and their configurations, see the [ForgeFlow Wiki](wiki/README.md):

- [Node Types](wiki/templates/node-types.md)
- [Connections](wiki/templates/connections.md)
- [Variables](wiki/templates/variables.md)

## Categories

Use one of these standard categories:

- **Automation** - File operations, scheduled tasks, scripts
- **Productivity** - Reminders, timers, organization tools
- **DevOps** - Monitoring, deployment, CI/CD
- **AI** - LLM integrations, chatbots, summarization
- **Data** - Parsing, transformations, conversions
- **Integration** - Webhooks, APIs, third-party services

## Pull Request Requirements

1. Fork the repository
2. Create a new branch: `git checkout -b add-template-name`
3. Add your template file to `templates/`
4. Update `index.json` with your template entry
5. Commit your changes: `git commit -m "Add [Template Name] template"`
6. Push to your fork: `git push origin add-template-name`
7. Open a Pull Request with:
   - Clear description of what your template does
   - Screenshots or GIFs showing the template in action (optional but appreciated)
   - Any special requirements or dependencies

## Code of Conduct

- Be respectful and constructive
- Provide helpful and accurate templates
- Test your templates before submitting
- Follow the established structure and conventions
- Help others by reviewing PRs and providing feedback

## Questions?

If you have questions about contributing, feel free to:
- Open an issue for discussion
- Check existing templates for examples
- Review the [ForgeFlow Wiki](wiki/README.md) for technical details

Thank you for contributing to the ForgeFlow community! 🎉
