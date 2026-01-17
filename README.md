# knowledge

A personal knowledge garden automatically syncing and organizing my Chrome and Firefox bookmarks, GitHub stars, cheatsheets, tldr, and other favorites and knowledge repositories from across the web.

## Features

- **GitHub Stars Sync** - Automatically fetches and organizes starred repositories
- **AI-Powered Organization** - Uses Claude to intelligently categorize content
- **Interactive Assistant** - Ask Claude questions about your knowledge base via `@claude` mentions
- **Scheduled Updates** - Daily automatic syncs keep everything current

## Repository Structure

```
knowledge/
├── stars/              # Organized GitHub stars by category
│   ├── README.md       # Overview and statistics
│   └── [category].md   # Category-specific collections
├── data/               # Raw and processed data
│   ├── stars-raw.json  # Raw GitHub API data
│   └── stars.json      # Processed/categorized data
├── bookmarks/          # Browser bookmarks (planned)
├── cheatsheets/        # Quick reference guides (planned)
└── .github/workflows/  # Automation workflows
```

## Setup

### Prerequisites

1. **Anthropic API Key** - Required for Claude Code Action
   - Get one at [console.anthropic.com](https://console.anthropic.com)
   - Add as `ANTHROPIC_API_KEY` in repository secrets

2. **GitHub Token** - Automatically provided by GitHub Actions
   - Default `GITHUB_TOKEN` has necessary permissions

### Repository Secrets

Add these secrets in Settings → Secrets and variables → Actions:

| Secret | Description | Required |
|--------|-------------|----------|
| `ANTHROPIC_API_KEY` | Your Anthropic API key | Yes |

## Usage

### Automatic Sync

Stars are synced automatically every day at midnight UTC.

### Manual Sync

1. Go to **Actions** → **Sync GitHub Stars**
2. Click **Run workflow**
3. Options:
   - **Full sync**: Re-categorize all stars (default: incremental)
   - **Dry run**: Preview changes without committing

### Interactive Commands

Mention `@claude` in any issue or PR comment:

```
@claude What TypeScript CLI tools have I starred?
@claude Find stars related to Kubernetes
@claude Show statistics for my starred repos
@claude Sync my stars now
```

## Workflows

### sync-stars.yml

Handles GitHub stars synchronization:

| Trigger | Description |
|---------|-------------|
| `schedule` | Daily at 00:00 UTC |
| `workflow_dispatch` | Manual trigger with options |
| `issue_comment` | `@claude` mentions in issues |
| `pull_request_review_comment` | `@claude` mentions in PRs |

## Star Categories

Stars are organized into logical categories:

| Category | Description |
|----------|-------------|
| Languages | TypeScript, Rust, Go, Python, etc. |
| CLI Tools | Command-line utilities |
| DevTools | Developer productivity tools |
| Frameworks | Web and app frameworks |
| Libraries | Reusable code libraries |
| AI/ML | Machine learning and AI tools |
| Infrastructure | Containers, cloud, networking |
| Learning | Tutorials, docs, awesome lists |
| Security | Security tools and resources |
| Data | Databases and analytics |

## Roadmap

- [x] GitHub stars sync workflow
- [ ] Chrome bookmarks sync
- [ ] Firefox bookmarks sync
- [ ] Cheatsheets collection
- [ ] TLDR pages integration
- [ ] Cross-source deduplication
- [ ] Search interface

## Contributing

Feel free to open issues or PRs! You can also interact with `@claude` directly in issues for assistance.

## License

MIT - See [LICENSE](LICENSE) for details.
