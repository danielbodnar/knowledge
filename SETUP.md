# Setup Guide

This guide will help you set up your knowledge garden repository with automated AI classification and organization.

## Prerequisites

- GitHub account
- Git installed locally
- (Optional) Anthropic API key for Claude Code Action
- (Optional) GitHub Copilot subscription

## Quick Start

### 1. Fork or Use This Repository

**Option A: Fork this repository**
```bash
# Click "Fork" on GitHub, then clone your fork
git clone https://github.com/YOUR_USERNAME/knowledge.git
cd knowledge
```

**Option B: Use as template**
- Click "Use this template" on GitHub
- Create your new repository
- Clone it locally

### 2. Configure GitHub Secrets

For automated AI classification, add your Anthropic API key:

1. Go to your repository on GitHub
2. Click Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Name: `ANTHROPIC_API_KEY`
5. Value: Your API key from https://console.anthropic.com/

### 3. Enable GitHub Actions

1. Go to Actions tab in your repository
2. Click "I understand my workflows, go ahead and enable them"
3. Workflows will now run automatically on push

### 4. (Optional) Enable GitHub Copilot

If you have GitHub Copilot:
1. Install VS Code and GitHub Copilot extension
2. Open the repository in VS Code
3. Copilot will automatically use the agent instructions in `.github/copilot/`

## Adding Your First Content

### Method 1: Using Templates

```bash
# Copy a template
cp templates/bookmark-template.md bookmarks/general/my-first-bookmark.md

# Edit the file
# Fill in the YAML frontmatter:
# - title
# - url
# - category
# - tags
# - date_added

# Commit and push
git add bookmarks/general/my-first-bookmark.md
git commit -m "Add my first bookmark"
git push
```

The AI will automatically:
- Validate and enhance metadata
- Ensure proper categorization
- Add missing tags
- Update index files

### Method 2: Quick Add (Manual)

Create a file directly:

```bash
cat > bookmarks/general/quick-add.md << 'EOF'
---
title: "GitHub Documentation"
url: "https://docs.github.com"
category: "Development"
tags: [git, github, documentation, reference]
date_added: "2026-01-17"
last_updated: "2026-01-17"
---

# GitHub Documentation

## Description

Official GitHub documentation covering repositories, actions, APIs, and more.

## Category

Development

## Tags

git, github, documentation, reference
EOF

git add bookmarks/general/quick-add.md
git commit -m "Add GitHub docs"
git push
```

## Importing Existing Bookmarks

### Chrome Bookmarks

1. Export bookmarks from Chrome:
   - Menu → Bookmarks → Bookmark manager
   - Click ⋮ (three dots) → Export bookmarks
   - Save as `bookmarks.html`

2. Convert to markdown (manual or scripted):

```bash
# Example Python script to convert (create your own or use a tool)
# This is a basic example - you'll want to enhance it

python - << 'EOF'
import re
from pathlib import Path
from datetime import datetime

# Read exported HTML
with open('bookmarks.html', 'r') as f:
    html = f.read()

# Extract bookmark entries (basic regex - adjust as needed)
pattern = r'<A HREF="([^"]+)"[^>]*>([^<]+)</A>'
bookmarks = re.findall(pattern, html)

# Create markdown files
for url, title in bookmarks[:10]:  # Start with first 10
    filename = re.sub(r'[^\w\s-]', '', title.lower())
    filename = re.sub(r'[-\s]+', '-', filename)
    
    content = f"""---
title: "{title}"
url: "{url}"
category: "Learning"  # Adjust as needed
tags: [bookmark, imported]
date_added: "{datetime.now().strftime('%Y-%m-%d')}"
last_updated: "{datetime.now().strftime('%Y-%m-%d')}"
---

# {title}

## Description

Imported bookmark - needs review and classification.

## URL

{url}
"""
    
    Path(f"bookmarks/general/{filename}.md").write_text(content)

print(f"Imported {len(bookmarks[:10])} bookmarks")
EOF
```

3. Push and let AI classify:

```bash
git add bookmarks/general/
git commit -m "Import Chrome bookmarks"
git push
```

### Firefox Bookmarks

Similar process:
1. Menu → Bookmarks → Manage bookmarks
2. Import and Backup → Export Bookmarks to HTML
3. Use similar conversion script

### GitHub Stars

Option 1: Manual entry using template
```bash
cp templates/github-star-template.md github-stars/repo-name.md
# Edit and fill in details
```

Option 2: Use GitHub API (example script):

```bash
# Requires: gh CLI or API token
# This fetches your starred repos

python - << 'EOF'
import requests
import os
from datetime import datetime
from pathlib import Path

token = os.getenv('GITHUB_TOKEN')
headers = {'Authorization': f'token {token}'}

# Get starred repos
url = 'https://api.github.com/user/starred?per_page=10'
response = requests.get(url, headers=headers)
repos = response.json()

for repo in repos:
    name = repo['name']
    full_name = repo['full_name']
    desc = repo['description'] or 'No description'
    url = repo['html_url']
    stars = repo['stargazers_count']
    lang = repo['language'] or 'Unknown'
    
    content = f"""---
repo_name: "{full_name}"
repo_url: "{url}"
owner: "{repo['owner']['login']}"
category: "Development"
tags: [github, starred, {lang.lower() if lang != 'Unknown' else 'misc'}]
stars: {stars}
language: "{lang}"
date_starred: "{datetime.now().strftime('%Y-%m-%d')}"
last_updated: "{datetime.now().strftime('%Y-%m-%d')}"
---

# {name}

## Description

{desc}

## Why Starred

[Add your reason for starring this repository]

## Category

Development

## Tags

github, starred, {lang.lower() if lang != 'Unknown' else 'misc'}
"""
    
    filename = name.lower().replace(' ', '-')
    Path(f"github-stars/{filename}.md").write_text(content)

print(f"Imported {len(repos)} starred repos")
EOF
```

## Customization

### Customize Categories

Edit categories in:
- `.github/copilot/classifier-instructions.md`
- `STRUCTURE.md`
- Workflow prompts in `.github/workflows/classify-knowledge.yml`

Example: Add "Gaming" category:

1. Update classifier instructions
2. Add to STRUCTURE.md
3. Create `bookmarks/gaming/` directory
4. Update workflow prompts to include "Gaming"

### Customize Tags

Edit `TAGS.md` to:
- Add new approved tags
- Define tag categories
- Set naming standards

### Customize Templates

Edit files in `templates/` to match your needs:
- Add custom fields
- Change format
- Add sections
- Modify metadata

### Customize Workflows

Edit `.github/workflows/*.yml` to:
- Change trigger conditions
- Modify classification prompts
- Adjust commit messages
- Add new automation steps

## Using GitHub Copilot

With GitHub Copilot enabled in VS Code:

```
# In Copilot Chat:

@workspace Classify the new bookmarks I added

@workspace Organize the cheatsheets directory by technology

@workspace Add proper tags to all Python content

@workspace Create an index for the DevOps category
```

The agents in `.github/copilot/` provide specialized knowledge.

## Maintenance

### Regular Tasks

**Weekly**:
```bash
# Review and commit any local changes
git status
git add -A
git commit -m "Weekly update"
git push
```

**Monthly**:
- Review auto-generated indices
- Clean up duplicates
- Update outdated links
- Archive old content

**Quarterly**:
- Review and update categories
- Consolidate tags
- Major reorganization if needed

### Updating the Repository

Pull latest changes from upstream (if using template):

```bash
# Add upstream remote (one time)
git remote add upstream https://github.com/ORIGINAL_OWNER/knowledge.git

# Update from upstream
git fetch upstream
git merge upstream/main
```

## Troubleshooting

### Workflows Not Running

1. Check Actions are enabled (Settings → Actions)
2. Verify secrets are set correctly
3. Check workflow file syntax (YAML)
4. Review workflow logs for errors

### AI Classification Not Working

1. Verify `ANTHROPIC_API_KEY` is set
2. Check API quota/limits
3. Review Claude API status
4. Check workflow logs

### Copilot Not Using Instructions

1. Ensure files are in `.github/copilot/`
2. Use `@workspace` in prompts
3. Reload VS Code window
4. Check Copilot extension is active

## Advanced Setup

### Custom Domain for GitHub Pages

1. Enable GitHub Pages in repository settings
2. Create a custom index page
3. Add CNAME file with your domain
4. Configure DNS

### Sync with External Sources

Create scheduled workflows to:
- Import browser bookmarks automatically
- Sync GitHub stars daily
- Backup to external storage
- Generate reports

### Integration with Other Tools

- Export to Notion, Obsidian, or other note apps
- Create RSS feeds for updates
- Generate static site with Jekyll/Hugo
- Set up search with Algolia

## Next Steps

1. ✅ Setup complete
2. 📝 Add your first few items
3. 🤖 Watch AI organize them
4. 🔍 Explore and refine
5. 📚 Build your knowledge garden!

## Resources

- [README.md](README.md) - Repository overview
- [STRUCTURE.md](STRUCTURE.md) - Organization details
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contribution guide
- [TAGS.md](TAGS.md) - Tag vocabulary
- [.github/workflows/README.md](.github/workflows/README.md) - Workflow docs
- [.github/copilot/README.md](.github/copilot/README.md) - Copilot agent docs

## Getting Help

- Open an issue for bugs or questions
- Check existing issues for solutions
- Review documentation files
- Contribute improvements back!

Happy organizing! 🌱
