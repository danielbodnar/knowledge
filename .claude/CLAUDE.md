# CLAUDE.md - Knowledge Garden Instructions

This repository is a personal knowledge garden that automatically syncs and organizes various sources including GitHub stars, bookmarks, and other knowledge resources.

## Repository Structure

```
knowledge/
├── data/              # Raw and processed data files
│   ├── stars-raw.json # Raw GitHub stars data (auto-fetched)
│   └── stars.json     # Processed/categorized stars data
├── stars/             # Organized star documentation
│   ├── README.md      # Overview and table of contents
│   └── [category].md  # Category-specific files
├── bookmarks/         # Browser bookmarks (future)
├── cheatsheets/       # Quick reference guides (future)
└── .github/workflows/ # Automation workflows
```

## Star Organization Guidelines

When organizing GitHub stars, follow these principles:

### Categories

Organize stars into these primary categories:

1. **Languages** - Group by primary programming language when meaningful
   - `typescript.md`, `rust.md`, `go.md`, `python.md`, etc.
   - Only create language files for languages with 5+ starred repos

2. **Tools** - Developer tools and utilities
   - `cli-tools.md` - Command-line tools
   - `devtools.md` - Development utilities
   - `productivity.md` - Productivity tools

3. **Libraries & Frameworks**
   - `frameworks.md` - Web/app frameworks
   - `libraries.md` - Reusable code libraries

4. **Infrastructure**
   - `containers.md` - Docker, Kubernetes, etc.
   - `cloud.md` - Cloud providers, serverless
   - `networking.md` - Network tools

5. **AI & ML**
   - `ai-ml.md` - Machine learning, AI tools
   - `llm.md` - Large language models, prompts

6. **Learning**
   - `learning.md` - Tutorials, courses
   - `awesome-lists.md` - Curated lists
   - `documentation.md` - Reference docs

7. **Specialized**
   - `security.md` - Security tools
   - `data.md` - Databases, analytics
   - `ui-design.md` - UI/UX tools

### Formatting Standards

Each category file should follow this format:

```markdown
# [Category Name]

> [Brief description of this category]

## Quick Stats
- Total repos: X
- Most starred: [repo] (X stars)
- Recently updated: [repo]

## Repositories

### [Repository Name](url)
![Stars](badge) ![Language](badge)

> Description from GitHub

- **Topics:** tag1, tag2, tag3
- **Last Updated:** YYYY-MM-DD
- **License:** MIT/Apache/etc.

---
```

### stars/README.md Structure

```markdown
# GitHub Stars

> Automatically organized collection of starred repositories

## Summary
- **Total Stars:** X
- **Categories:** X
- **Last Synced:** YYYY-MM-DD

## Categories

| Category | Count | Description |
|----------|-------|-------------|
| [TypeScript](typescript.md) | X | TypeScript libraries and tools |
| ... | ... | ... |

## Recent Stars

1. [repo](url) - description
2. ...

## Statistics

### By Language
- TypeScript: X
- Rust: X
- ...

### Most Starred
1. [repo](url) - X stars
2. ...
```

## Interactive Commands

When users mention @claude in issues or PRs, respond helpfully:

- **Search:** "Find me stars related to X" - Search and list matching repos
- **Summarize:** "Summarize the X category" - Provide overview
- **Recommend:** "What tools for Y?" - Recommend relevant starred repos
- **Stats:** "Show star statistics" - Display analytics

## Data Processing

### Input Format (stars-raw.json)
```json
[
  {
    "starredAt": "2024-01-15T...",
    "node": {
      "nameWithOwner": "owner/repo",
      "description": "...",
      "url": "https://github.com/...",
      "primaryLanguage": { "name": "TypeScript" },
      "repositoryTopics": { "nodes": [{ "topic": { "name": "cli" } }] },
      "stargazerCount": 1000,
      "forkCount": 100,
      "isArchived": false,
      "updatedAt": "2024-01-10T...",
      "licenseInfo": { "spdxId": "MIT" }
    }
  }
]
```

### Output Format (stars.json)
```json
{
  "lastSynced": "2024-01-15T...",
  "totalStars": 500,
  "categories": {
    "typescript": {
      "name": "TypeScript",
      "description": "TypeScript libraries and tools",
      "count": 50,
      "repos": ["owner/repo", ...]
    }
  },
  "repos": {
    "owner/repo": {
      "name": "repo",
      "owner": "owner",
      "description": "...",
      "url": "...",
      "language": "TypeScript",
      "topics": ["cli", "typescript"],
      "stars": 1000,
      "forks": 100,
      "archived": false,
      "updatedAt": "...",
      "license": "MIT",
      "categories": ["typescript", "cli-tools"],
      "starredAt": "..."
    }
  }
}
```

## Best Practices

1. **Incremental Updates** - Only update changed content
2. **Preserve Manual Edits** - Don't overwrite user-added notes
3. **Consistent Formatting** - Use consistent markdown style
4. **Useful Links** - Include GitHub badges where helpful
5. **Clean Output** - Remove archived repos to separate section

## Tools Available

- `Bash` - Run shell commands, use `gh api` for GitHub queries
- `Read` - Read files from the repository
- `Write` - Create or overwrite files
- `Edit` - Make targeted edits to existing files
- `Glob` - Find files by pattern
- `Grep` - Search file contents
