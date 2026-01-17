# GitHub Actions Workflows

This directory contains automated workflows that maintain and organize the knowledge repository.

## Workflows

### 1. AI-Powered Classification
**File**: `classify-knowledge.yml`

**Trigger**: 
- Push to main/master branch
- Pull requests
- Only when files in knowledge directories change

**What It Does**:
- Uses Claude Code Action (Anthropic AI) to analyze changes
- Classifies new/modified content
- Adds or updates metadata (categories, tags)
- Ensures consistent formatting
- Moves files to appropriate directories
- Updates index files

**Requirements**:
- `ANTHROPIC_API_KEY` secret must be set
- `GITHUB_TOKEN` (automatically provided)

**Configuration**:
```yaml
paths:
  - 'bookmarks/**'
  - 'github-stars/**'
  - 'cheatsheets/**'
  - 'tldr/**'
  - 'favorites/**'
```

### 2. Auto-Label and Organize
**File**: `auto-organize.yml`

**Trigger**:
- Push to main/master
- Pull requests (opened, synchronized, reopened)

**What It Does**:

**Job 1: auto-label**
- Automatically labels PRs based on file paths
- Uses `.github/labeler.yml` configuration
- Adds content-type labels (bookmarks, cheatsheets, etc.)
- Adds technology labels (docker, kubernetes, python, etc.)

**Job 2: reorganize-content**
- Generates index files for all directories
- Updates auto-generated sections in READMEs
- Organizes content by category and date
- Runs only on push to main/master

**Requirements**:
- `GITHUB_TOKEN` (automatically provided)
- Python 3.11+
- Dependencies: pyyaml, requests

## Workflow Features

### Automatic Classification

When you add a new file, Claude AI:
1. Reads the content and URL
2. Identifies the topic and category
3. Generates appropriate tags
4. Adds/updates YAML frontmatter
5. Determines optimal directory location
6. Commits changes with `[skip ci]` tag

### Automatic Labeling

PRs are labeled based on:
- **File paths**: bookmarks/, cheatsheets/, etc.
- **Content keywords**: docker, kubernetes, python
- **File types**: documentation, automation

Labels help with:
- Quick PR categorization
- Filtering and search
- Automated workflows
- Issue tracking

### Index Generation

The workflow automatically:
- Scans all markdown files
- Reads YAML frontmatter
- Groups by category
- Sorts by date
- Generates organized lists
- Appends to README files

## Setup Instructions

### 1. Configure Secrets

In GitHub repository settings → Secrets and variables → Actions:

```
ANTHROPIC_API_KEY = your_anthropic_api_key_here
```

Get your API key from: https://console.anthropic.com/

### 2. Configure Labels

The labeler uses `.github/labeler.yml`. Edit to customize:

```yaml
bookmarks:
  - 'bookmarks/**/*'

python:
  - '**/*.py'
  - '**/*python*'
```

### 3. Customize Workflows

Edit workflow files to:
- Change trigger conditions
- Adjust file path patterns
- Modify classification prompts
- Change commit messages
- Update Python scripts

## Workflow Execution

### On Push

```
1. Code pushed to main
2. classify-knowledge.yml runs
   - Claude analyzes changes
   - Updates metadata
   - Commits improvements [skip ci]
3. auto-organize.yml runs
   - Labels are applied
   - Indices are updated
   - Changes committed [skip ci]
```

### On Pull Request

```
1. PR opened/updated
2. classify-knowledge.yml runs
   - Analyzes PR changes
   - Suggests improvements
3. auto-label job runs
   - Applies labels to PR
4. reorganize-content skipped
   (runs only on merge to main)
```

## Workflow Permissions

Both workflows require:

```yaml
permissions:
  contents: write      # To commit changes
  pull-requests: write # To label PRs
  issues: write        # To label issues
```

## Skipping Workflows

Use `[skip ci]` in commit messages to prevent workflow runs:

```bash
git commit -m "Update README [skip ci]"
```

This is useful for:
- Documentation-only changes
- Preventing infinite loops
- Manual maintenance commits

## Monitoring Workflows

### Check Workflow Status

1. Go to repository → Actions tab
2. View recent workflow runs
3. Click run to see detailed logs
4. Check for errors or warnings

### Common Issues

**Claude API Key Error**:
- Verify `ANTHROPIC_API_KEY` is set correctly
- Check API key has sufficient quota
- Ensure secret name matches workflow

**Permission Denied**:
- Verify workflow permissions are correct
- Check `GITHUB_TOKEN` has necessary scopes
- Review branch protection rules

**Python Script Errors**:
- Check Python version (3.11+)
- Verify dependencies are installed
- Review YAML frontmatter format

## Customization Examples

### Change Classification Prompt

Edit `classify-knowledge.yml`:

```yaml
- name: Claude Code Action - Auto-classify
  uses: anthropics/claude-code-action@v1
  with:
    prompt: |
      Your custom classification instructions here.
      Be specific about what you want Claude to do.
```

### Add Custom Labels

Edit `.github/labeler.yml`:

```yaml
rust:
  - '**/*.rs'
  - '**/*rust*'

security:
  - '**/*security*'
  - '**/*auth*'
```

### Modify Index Format

Edit the Python script in `auto-organize.yml`:

```python
f.write(f"- [{title}]({path}) - {category}\n")
# Change to your preferred format
```

## Best Practices

1. **Test Workflows**: Test in a fork or feature branch first
2. **Monitor Runs**: Check workflow results regularly
3. **Review Changes**: Review AI-generated changes before merging
4. **Update Prompts**: Refine classification prompts over time
5. **Keep Secrets Secure**: Never commit API keys
6. **Use [skip ci]**: Prevent unnecessary runs

## Debugging

### Enable Debug Logging

Add to workflow:

```yaml
env:
  ACTIONS_STEP_DEBUG: true
  ACTIONS_RUNNER_DEBUG: true
```

### View Full Logs

```bash
# Download logs using GitHub CLI
gh run view RUN_ID --log
```

### Test Locally

```bash
# Test Python index generation
python .github/workflows/scripts/generate_index.py

# Validate YAML
yamllint .github/workflows/*.yml
```

## Future Enhancements

Potential additions:
- Sync with browser bookmarks APIs
- Import GitHub stars automatically
- Generate visualizations/stats
- Check for broken links
- Archive outdated content
- Generate tag clouds
- Create weekly summaries

## Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Claude Code Action](https://github.com/anthropics/claude-code-action)
- [GitHub Labeler Action](https://github.com/actions/labeler)
- [YAML Syntax](https://yaml.org/spec/)
