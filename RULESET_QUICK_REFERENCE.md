# GitHub Rulesets - Quick Configuration Guide

## Quick Reference: What to Enable

When creating a **New branch ruleset** for your `main` branch, enable these checkboxes:

### Essential Rules (Must Enable)
```
☑️  Restrict updates
    └─ Only allow users with bypass permission to update matching refs

☑️  Restrict deletions  
    └─ Only allow users with bypass permissions to delete matching refs

☑️  Block force pushes
    └─ Prevent users with push access from force pushing to refs

☑️  Require a pull request before merging
    └─ Required approvals: 1
    ├─ ☑️  Dismiss stale pull request approvals when new commits are pushed
    ├─ ☑️  Require approval of the most recent reviewable push
    └─ ☑️  Require conversation resolution before merging
```

### Recommended Rules (Should Enable)
```
☑️  Require linear history
    └─ Prevent merge commits from being pushed to matching refs
    (Keeps commit history clean)

☑️  Require review from Code Owners
    └─ (Only if you have a CODEOWNERS file)
```

### Optional Rules (Can Skip)
- Require status checks to pass (if no CI/CD)
- Require signed commits (for extra security)
- Require deployments to succeed (if using deploy environments)

## Configuration Steps

1. Go to Settings → Rules
2. Click "New ruleset" → "New branch ruleset"
3. **Ruleset Name**: `GitHub Branch Protection Rules`
4. **Enforcement status**: Active (default)
5. **Bypass list**: Leave empty
6. **Branch targeting**: Default (targets main branch)
7. **Enable rules** (see Essential list above)
8. Click **Create**

## Result

✅ Contributors must use pull requests  
✅ All PRs require at least 1 review  
✅ No force pushes to main  
✅ No direct edits to main branch  
✅ Clean, linear commit history  

---

**Full documentation**: See `BRANCH_PROTECTION_SETUP.md`
