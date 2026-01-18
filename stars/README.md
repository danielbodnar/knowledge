# GitHub Stars

> Automatically organized collection of starred repositories

## Summary

This directory will be populated when the sync workflow runs.

- **Total Stars:** Pending sync
- **Categories:** Pending sync
- **Last Synced:** Never

## How It Works

1. The GitHub Actions workflow fetches all starred repositories
2. Claude analyzes and categorizes them based on language, topics, and description
3. Results are organized into category files in this directory

## Triggering a Sync

### Manual Sync
Go to Actions → Sync GitHub Stars → Run workflow

### Scheduled
Runs automatically every day at midnight UTC

### Interactive
Comment `@claude` on any issue to discuss or refine categories for your starred repositories. This does not trigger the sync workflow; use the Manual or Scheduled options above for syncing.

## Categories

Categories will appear here after the first sync:

- `typescript.md` - TypeScript libraries and tools
- `rust.md` - Rust projects
- `cli-tools.md` - Command-line tools
- `devtools.md` - Developer tools
- `ai-ml.md` - AI and machine learning
- `learning.md` - Tutorials and documentation
- And more...
