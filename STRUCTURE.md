# Knowledge Repository Structure

This repository is organized as a knowledge garden, automatically syncing and organizing bookmarks, GitHub stars, cheatsheets, and other knowledge resources.

## Directory Structure

```
knowledge/
├── bookmarks/           # Browser bookmarks
│   ├── chrome/         # Chrome bookmarks
│   ├── firefox/        # Firefox bookmarks
│   └── general/        # General/uncategorized bookmarks
├── github-stars/        # Starred GitHub repositories
├── cheatsheets/         # Technical cheatsheets and quick references
├── tldr/               # TLDR summaries and quick guides
├── favorites/          # Other favorites and knowledge repositories
├── templates/          # Templates for adding new content
└── .github/            # GitHub configuration
    ├── workflows/      # GitHub Actions workflows
    └── copilot/        # GitHub Copilot agent instructions
```

## Content Organization

### Categories

Content is organized using the following primary categories:

- **Development**: Programming languages, frameworks, tools
- **DevOps**: Infrastructure, CI/CD, deployment, containers
- **Security**: Security practices, tools, guidelines
- **Design**: UI/UX, design systems, patterns
- **Data**: Databases, data science, analytics
- **AI/ML**: Artificial intelligence, machine learning
- **Cloud**: Cloud platforms, services, architecture
- **Productivity**: Tools, workflows, best practices
- **Learning**: Tutorials, courses, documentation
- **Reference**: APIs, specifications, standards

### Tags

Content can be tagged with multiple tags for better discoverability:
- Language-specific: `python`, `javascript`, `go`, `rust`, etc.
- Technology: `docker`, `kubernetes`, `react`, `vue`, etc.
- Topic: `testing`, `performance`, `monitoring`, `auth`, etc.

### Metadata

Each knowledge item includes metadata:
- **Title**: Clear, descriptive title
- **URL**: Original source URL
- **Category**: Primary category
- **Tags**: Multiple tags for cross-referencing
- **Description**: Brief description of content
- **Date Added**: When the item was added
- **Last Updated**: When the item was last reviewed/updated

## Automated Classification

This repository uses AI-powered classification to automatically:
1. Categorize new bookmarks and resources
2. Extract relevant tags
3. Generate descriptions
4. Organize content into appropriate directories
5. Update indexes and navigation

The classification is performed by:
- GitHub Copilot Agents
- Claude Code Action (Anthropic)
- OpenCode AI assistants

These tools run on every commit/push to maintain organization.
