# 🌱 Knowledge Garden

A personal knowledge garden automatically syncing and organizing my Chrome and Firefox bookmarks, GitHub stars, cheatsheets, TLDR guides, and other favorites from across the web.

## ✨ Features

- **🤖 AI-Powered Classification**: Automatically categorizes and tags new content using GitHub Copilot, Claude Code Action, and OpenCode
- **⭐ GitHub Stars Sync**: Automatically fetches and organizes starred repositories with AI-powered categorization
- **📚 Organized Structure**: Well-organized directory structure with categories and tags
- **🔍 Easy Discovery**: Search and filter by categories, tags, and content type
- **📝 Consistent Format**: Standardized templates for all content types
- **🔄 Automatic Sync**: GitHub Actions workflows for continuous organization
- **🏷️ Smart Labeling**: Automatic PR and issue labeling based on content
- **💬 Interactive Assistant**: Ask Claude questions about your knowledge base via `@claude` mentions

## 📁 Repository Structure

```
knowledge/
├── bookmarks/           # Browser bookmarks (Chrome, Firefox, general)
├── github-stars/        # Starred GitHub repositories (legacy)
├── stars/              # Organized GitHub stars by category (new)
│   ├── README.md       # Overview and statistics
│   └── [category].md   # Category-specific collections
├── cheatsheets/         # Technical cheatsheets and quick references
├── tldr/               # TLDR summaries and quick guides
├── favorites/          # Other favorites and knowledge repositories
├── data/               # Raw and processed data
│   ├── stars-raw.json  # Raw GitHub API data
│   └── stars.json      # Processed/categorized data
├── templates/          # Templates for adding new content
└── .github/            # GitHub Actions and Copilot configurations
```

## 🗂️ Categories

Content is organized into these primary categories:

- **Development**: Programming languages, frameworks, tools
- **DevOps**: CI/CD, infrastructure, deployment, containers
- **Security**: Security practices, tools, guidelines
- **Design**: UI/UX, design systems, patterns
- **Data**: Databases, data science, analytics
- **AI/ML**: Artificial intelligence, machine learning
- **Cloud**: Cloud platforms, services, architecture
- **Productivity**: Tools, workflows, best practices
- **Learning**: Tutorials, courses, documentation
- **Reference**: APIs, specifications, standards

## 🚀 Getting Started

### Adding Content Manually

1. **Use Templates**: Start with templates from the `/templates/` directory
2. **Add Metadata**: Fill in the YAML frontmatter with title, URL, category, tags
3. **Place in Directory**: Put the file in the appropriate category directory
4. **Commit**: The AI classification system will automatically organize and enhance

### Example: Adding a Bookmark

```bash
# Copy the template
cp templates/bookmark-template.md bookmarks/general/my-new-bookmark.md

# Edit the file with your content
# Add, commit, and push
git add bookmarks/general/my-new-bookmark.md
git commit -m "Add new bookmark"
git push
```

The automated workflows will:
- ✅ Classify the content into the correct category
- ✅ Generate relevant tags
- ✅ Update index files
- ✅ Add appropriate labels to the PR

### GitHub Stars Sync

Stars are synced automatically every day at midnight UTC.

#### Manual Sync

1. Go to **Actions** → **Sync GitHub Stars**
2. Click **Run workflow**
3. Options:
   - **Full sync**: Re-categorize all stars (default: incremental)
   - **Dry run**: Preview changes without committing

#### Interactive Commands

Mention `@claude` in any issue or PR comment:

```
@claude What TypeScript CLI tools have I starred?
@claude Find stars related to Kubernetes
@claude Show statistics for my starred repos
@claude Sync my stars now
```

## 🤖 Automated Classification

This repository uses multiple AI systems for automatic organization:

### GitHub Actions Workflows

1. **AI-Powered Classification** (`.github/workflows/classify-knowledge.yml`)
   - Uses Claude Code Action to classify new content
   - Runs on every push to knowledge directories
   - Automatically categorizes, tags, and organizes

2. **Auto-Label and Organize** (`.github/workflows/auto-organize.yml`)
   - Automatically labels PRs and issues
   - Generates and updates index files
   - Reorganizes content as needed

3. **Sync GitHub Stars** (`.github/workflows/sync-stars.yml`)
   - Fetches starred repositories from GitHub
   - Uses Claude to intelligently categorize stars
   - Runs on schedule (daily) and manual triggers
   - Supports `@claude` mentions in issues/PRs

**Triggers:**
| Trigger | Description |
|---------|-------------|
| `schedule` | Daily at 00:00 UTC |
| `workflow_dispatch` | Manual trigger with options |
| `issue_comment` | `@claude` mentions in issues |
| `pull_request_review_comment` | `@claude` mentions in PRs |

### GitHub Copilot Agents

Three specialized agents with custom instructions:

1. **Classifier** (`.github/copilot/classifier-instructions.md`)
   - Categorizes content into primary categories
   - Generates relevant tags
   - Ensures consistent metadata

2. **Organizer** (`.github/copilot/organizer-instructions.md`)
   - Maintains directory structure
   - Updates index files
   - Manages cross-references

3. **Tagger** (`.github/copilot/tagger-instructions.md`)
   - Applies consistent tags
   - Maintains tag vocabulary
   - Enables better searchability

## 🔧 Configuration

### Required Secrets

Set these secrets in your GitHub repository settings (Settings → Secrets and variables → Actions):

| Secret | Description | Required |
|--------|-------------|----------|
| `ANTHROPIC_API_KEY` | Your Anthropic API key for Claude Code Action | Yes |
| `GITHUB_TOKEN` | Automatically provided by GitHub Actions | Auto |

**Get your Anthropic API key:** [console.anthropic.com](https://console.anthropic.com)

### Workflow Customization

Edit workflow files in `.github/workflows/` to customize:
- Trigger conditions
- Classification rules
- Organization patterns
- Index generation

## 📖 Documentation

- [STRUCTURE.md](STRUCTURE.md) - Detailed structure documentation
- [SETUP.md](SETUP.md) - Setup instructions
- [INDEX.md](INDEX.md) - Content index
- [TAGS.md](TAGS.md) - Tag reference
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contribution guidelines
- [templates/](templates/) - Content templates
- [.github/copilot/](/.github/copilot/) - AI agent instructions

## 🏷️ Tags

Content is tagged with multiple dimensions:
- **Technology**: `python`, `javascript`, `docker`, `kubernetes`
- **Domain**: `web-development`, `machine-learning`, `cloud-computing`
- **Use Case**: `testing`, `monitoring`, `deployment`, `security`
- **Type**: `tutorial`, `documentation`, `tool`, `library`
- **Level**: `beginner`, `intermediate`, `advanced`

## 🔍 Search and Filter

Find content by:
- **Category**: Browse by primary category
- **Tags**: Filter by technology, use case, or type
- **Full-text search**: Search within content
- **Index files**: Browse organized README files in each directory

## ⭐ Star Categories

GitHub stars are organized into logical categories:

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

## 🗺️ Roadmap

- [x] GitHub stars sync workflow
- [x] AI-powered classification system
- [x] GitHub Copilot agents
- [x] Bookmarks structure
- [x] Cheatsheets collection
- [x] TLDR guides
- [ ] Chrome bookmarks sync
- [ ] Firefox bookmarks sync
- [ ] Cross-source deduplication
- [ ] Search interface
- [ ] Web dashboard

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add your content using the templates
4. Submit a pull request
5. Let the AI classification system do the rest!

Feel free to open issues or PRs! You can also interact with `@claude` directly in issues for assistance.

## 📊 Stats

- Total Resources: Updated automatically
- Categories: 10 primary categories
- AI Agents: 3 specialized agents
- Workflows: 3 automation workflows

## 📜 License

MIT - See [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- Built with [GitHub Copilot](https://github.com/features/copilot)
- Powered by [Claude Code Action](https://github.com/anthropics/claude-code-action)
- Organized with GitHub Actions

---

*Last updated: 2026-01-17*
