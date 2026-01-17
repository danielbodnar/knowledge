# GitHub Copilot Agent Instructions

This directory contains instruction files for GitHub Copilot agents that help maintain and organize this knowledge repository.

## Available Agents

### 1. Classifier Agent
**File**: `classifier-instructions.md`

**Purpose**: Automatically classify and categorize new content added to the repository.

**Capabilities**:
- Assigns primary category from approved list
- Generates relevant tags (3-7 per resource)
- Ensures metadata completeness
- Validates YAML frontmatter
- Adds descriptions when missing

**When to Use**:
- Adding new bookmarks
- Importing GitHub stars
- Creating new cheatsheets
- Any new content that needs classification

**Example Prompt**:
```
@workspace /classify Please classify the new bookmarks I added and ensure they have proper metadata and tags.
```

### 2. Organizer Agent
**File**: `organizer-instructions.md`

**Purpose**: Maintain repository structure and organization.

**Capabilities**:
- Creates/updates directory structures
- Reorganizes misplaced files
- Updates index files (README.md)
- Manages cross-references
- Ensures naming consistency

**When to Use**:
- Reorganizing content
- Creating new categories
- Updating navigation
- Cleaning up file structure

**Example Prompt**:
```
@workspace /organize Please reorganize the cheatsheets directory and update all index files.
```

### 3. Tagger Agent
**File**: `tagger-instructions.md`

**Purpose**: Apply consistent, meaningful tags to all content.

**Capabilities**:
- Generates appropriate tags
- Maintains tag vocabulary
- Ensures tag consistency
- Validates tag format
- Suggests related tags

**When to Use**:
- Adding tags to existing content
- Updating tag vocabulary
- Improving searchability
- Tag maintenance and cleanup

**Example Prompt**:
```
@workspace /tag Please review and improve tags for all Python-related content.
```

## Using GitHub Copilot Agents

### In VS Code

1. Open the repository in VS Code with GitHub Copilot enabled
2. Open the Copilot chat panel
3. Reference the workspace with `@workspace`
4. Use custom commands (if configured) or natural language prompts

### Example Workflows

#### Classifying New Content
```
User: I just added 5 new bookmarks to the bookmarks/general/ directory.

Copilot: @workspace Based on the classifier instructions, I'll analyze 
these bookmarks and classify them properly.

[Copilot reads the files, applies appropriate categories and tags]
```

#### Organizing Structure
```
User: The cheatsheets directory is getting messy. Can you organize it?

Copilot: @workspace I'll organize the cheatsheets by creating subdirectories
for different technologies and updating the index.

[Copilot creates subdirectories, moves files, updates READMEs]
```

#### Tag Maintenance
```
User: Please ensure all Docker-related content has consistent tags.

Copilot: @workspace I'll review all Docker content and standardize the tags
according to the tag vocabulary in TAGS.md.

[Copilot updates tags across multiple files]
```

## Custom Instructions Integration

These instruction files work with GitHub Copilot's workspace context to provide specialized knowledge about:

- Repository structure and conventions
- Category definitions
- Tag vocabulary and standards
- Metadata requirements
- Organization principles

## Agent Configuration

The agents are configured through:

1. **Instruction Files**: Detailed guidelines in this directory
2. **Tag Vocabulary**: `/TAGS.md` - Approved tag list
3. **Structure Guide**: `/STRUCTURE.md` - Organization principles
4. **Templates**: `/templates/` - Content templates
5. **Examples**: Existing well-formatted content

## Best Practices

### When Using Agents

1. **Be Specific**: Clear, specific prompts get better results
2. **Reference Context**: Use `@workspace` to include repository context
3. **Review Changes**: Always review agent suggestions before committing
4. **Iterate**: Refine prompts if results aren't quite right
5. **Document**: Update instructions if you discover better patterns

### Maintaining Instructions

- Keep instructions up-to-date with repository evolution
- Add examples when discovering new patterns
- Document edge cases and special handling
- Sync with actual repository structure
- Update based on user feedback

## Automation Integration

These agents work alongside GitHub Actions workflows:

```
User commits → GitHub Actions → AI Classification → Agents organize
```

The agents provide:
- Interactive help during development
- On-demand organization
- Quick classification
- Manual refinement

While GitHub Actions provide:
- Automatic processing on push
- Batch updates
- Scheduled maintenance
- CI/CD integration

## Troubleshooting

### Agent Not Following Instructions

1. Check that instruction file is up-to-date
2. Ensure you're using `@workspace` in prompts
3. Verify examples in instructions are accurate
4. Be more specific in your prompt

### Inconsistent Results

1. Review recent changes to instruction files
2. Check tag vocabulary is current
3. Verify template files are consistent
4. Update examples to reflect desired output

### Missing Context

1. Ensure all relevant files are in workspace
2. Reference specific instruction files if needed
3. Provide additional context in your prompt
4. Point to example files that demonstrate desired output

## Contributing

To improve agent instructions:

1. Test changes with actual use cases
2. Add clear examples
3. Document edge cases
4. Keep instructions concise
5. Submit PR with explanation

## Resources

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Copilot Workspace Commands](https://code.visualstudio.com/docs/copilot/workspace-context)
- [Repository STRUCTURE.md](/STRUCTURE.md)
- [Tag Vocabulary](/TAGS.md)
- [Contributing Guide](/CONTRIBUTING.md)
