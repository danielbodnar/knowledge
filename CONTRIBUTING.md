# Contributing to Knowledge Garden

Thank you for contributing to this knowledge repository! This guide will help you add and organize content effectively.

## 📝 How to Contribute

### Adding New Content

1. **Choose the Right Template**
   - Bookmark: `templates/bookmark-template.md`
   - GitHub Star: `templates/github-star-template.md`
   - Cheatsheet: `templates/cheatsheet-template.md`

2. **Fill in Metadata**
   - Complete all YAML frontmatter fields
   - Choose appropriate category
   - Add 3-7 relevant tags
   - Include date_added

3. **Write Quality Content**
   - Clear, concise descriptions
   - Useful notes or key takeaways
   - Related resources when applicable

4. **Place in Correct Directory**
   - `bookmarks/` for web bookmarks
   - `github-stars/` for GitHub repositories
   - `cheatsheets/` for quick references
   - `tldr/` for quick guides
   - `favorites/` for other resources

### Example Workflow

```bash
# 1. Create a new branch
git checkout -b add-resource-name

# 2. Copy template
cp templates/bookmark-template.md bookmarks/general/new-resource.md

# 3. Edit the file with your content

# 4. Commit and push
git add bookmarks/general/new-resource.md
git commit -m "Add new resource: Resource Name"
git push origin add-resource-name

# 5. Create pull request
# The AI will automatically classify and organize
```

## 🏷️ Metadata Guidelines

### Required Fields

```yaml
---
title: "Clear, Descriptive Title"
url: "https://example.com"
category: "One of the 10 primary categories"
tags: [tag1, tag2, tag3]
date_added: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
---
```

### Categories

Choose one primary category:
- Development
- DevOps
- Security
- Design
- Data
- AI/ML
- Cloud
- Productivity
- Learning
- Reference

### Tags

Include 3-7 tags covering:
- **Technology**: Specific tech (e.g., `python`, `react`, `docker`)
- **Domain**: Broader area (e.g., `web-development`, `cloud-computing`)
- **Use Case**: What it helps with (e.g., `testing`, `monitoring`)
- **Type**: Kind of resource (e.g., `tutorial`, `tool`, `documentation`)

**Tag Format**:
- All lowercase
- Use hyphens for multi-word: `machine-learning`
- Be specific: `react-hooks` vs `react`

## ✅ Quality Checklist

Before submitting, ensure:

- [ ] YAML frontmatter is complete and valid
- [ ] Category is from the approved list
- [ ] At least 3 relevant tags
- [ ] Description is clear and informative
- [ ] URL is valid (if applicable)
- [ ] No typos or formatting issues
- [ ] File is in appropriate directory
- [ ] Follows template structure

## 🤖 AI Classification

After you submit a PR, the AI classification system will:

1. **Validate metadata** - Check for completeness
2. **Enhance tags** - Add missing relevant tags
3. **Categorize** - Confirm or adjust category
4. **Organize** - Move to optimal directory if needed
5. **Update indices** - Add to relevant README files
6. **Label PR** - Apply appropriate labels

You may see automatic commits from `github-actions[bot]` with these improvements.

## 🔄 Updating Existing Content

To update existing resources:

1. Make your edits
2. Update `last_updated` field
3. Commit with descriptive message
4. The AI will validate and maintain organization

## 🌿 Best Practices

### Writing Descriptions

- **Be concise**: 1-2 sentences
- **Be specific**: What makes this resource valuable?
- **Be helpful**: Include key features or benefits

**Good**: "Comprehensive React testing library with intuitive API for writing maintainable tests. Focuses on testing behavior rather than implementation."

**Avoid**: "A testing library for React."

### Choosing Tags

**Good tags**: `react`, `testing`, `javascript`, `frontend`, `library`, `intermediate`

**Avoid**:
- Too generic: `programming`, `code`
- Too many: 15+ tags
- Too few: 1-2 tags
- Inconsistent format: `React`, `TESTING`, `Java Script`

### Related Resources

Link to related content within the repository:

```markdown
## Related Resources

- [Docker Cheatsheet](../../cheatsheets/docker-cheatsheet.md)
- [Kubernetes Documentation](kubernetes-docs.md)
- [DevOps Best Practices](../../learning/devops-practices.md)
```

## 📊 Content Organization

### Directory Structure

```
category/
  ├── README.md          # Index file
  ├── subcategory1/
  │   ├── README.md
  │   └── resource1.md
  └── subcategory2/
      ├── README.md
      └── resource2.md
```

### When to Create Subdirectories

- 10+ items in a category
- Clear logical grouping
- Different subcategories needed

### Naming Conventions

**Files**:
- Lowercase with hyphens: `docker-best-practices.md`
- Descriptive: Include topic and type
- No special characters except `-` and `_`

**Directories**:
- Lowercase with hyphens: `web-development/`
- Plural for collections: `frameworks/`, `tutorials/`
- Singular for single concept: `security/`

## 🚫 What Not to Contribute

Avoid adding:

- Duplicate content (search first!)
- Broken or dead links
- Low-quality or spam resources
- Proprietary or copyrighted material
- Personal/private information
- Resources without clear value

## 💡 Tips

1. **Search first**: Check if resource already exists
2. **Use templates**: Maintains consistency
3. **Complete metadata**: Helps AI classification
4. **Be descriptive**: Help others discover content
5. **Link related items**: Build knowledge connections
6. **Update regularly**: Keep content fresh

## 🤔 Questions?

- Check [STRUCTURE.md](STRUCTURE.md) for organization details
- Review [README.md](README.md) for overview
- Look at existing content for examples
- Open an issue for questions

## 🎉 Recognition

Contributors are recognized in:
- Git history and commit logs
- PR acknowledgments
- Community building

Thank you for helping build this knowledge garden! 🌱
