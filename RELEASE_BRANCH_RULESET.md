# Release Branch Ruleset Configuration

This guide shows how to set up GitHub Rulesets for your `releases/*` branches to maintain quality and consistency across releases.

## Why Protect Release Branches?

Release branches deserve the same protection as `main`:
- ✅ Ensures code review before release
- ✅ Prevents accidental commits to release branch
- ✅ Maintains clean release history
- ✅ Enforces documentation updates

## Setup: Release Branch Ruleset

### Step 1: Create Release Branch Ruleset

1. Go to **Settings → Rules**
2. Click **New ruleset** → **New branch ruleset**

### Step 2: Configure for Release Branches

#### Basic Information
- **Ruleset Name**: `Release Branch Protection`
- **Enforcement status**: Active
- **Bypass list**: Leave empty

#### Target Branches
- **Branch targeting criteria**: Select **"By pattern"**
- **Branch pattern**: `releases/*`
  - This matches: `releases/1.0.0`, `releases/1.0.1`, `releases/2.0.0`, etc.

#### Rules Configuration

Enable these rules:

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

☑️  Require linear history (optional but recommended)
    └─ Prevents merge commits for clean history
```

### Step 3: Save Ruleset

Click **Create** button

## Result

Now your release branches:
- ✅ Cannot be pushed to directly
- ✅ Require PRs for any changes
- ✅ Require at least 1 approval before merging
- ✅ Cannot be force-pushed
- ✅ Maintain linear commit history

## Release Branch Workflow

With this setup, the release process becomes:

```bash
# 1. Create release branch from main
git checkout main
git pull origin main
git checkout -b releases/1.0.0

# 2. Make release updates (version bumps, changelog, etc.)
git add CHANGELOG.md README.md
git commit -m "chore: Prepare release 1.0.0"

# 3. Try to push (will be blocked by ruleset)
git push origin releases/1.0.0
# → You'll get error about branch protection

# 4. Create PR instead
# Go to GitHub → Pull Requests → New Pull Request
# Select: releases/1.0.0 → main

# 5. Approve and merge your own PR
# (You CAN approve your own release PR)

# 6. Create GitHub Release tag
# Go to Releases → New Release → tag v1.0.0
```

## Multiple Rulesets Summary

| Ruleset | Pattern | Purpose |
|---------|---------|---------|
| Main Branch Protection | `main` | Protect primary codebase |
| Release Branch Protection | `releases/*` | Protect release branches |

Both enforce:
- ✅ Pull request reviews
- ✅ No direct commits
- ✅ No force pushes
- ✅ Linear history

## Release Checklist with Rulesets

Before starting release:

1. **Prepare Release Branch**
   ```bash
   git checkout main
   git checkout -b releases/1.0.0
   ```

2. **Update Documentation**
   - [ ] CHANGELOG.md with all changes
   - [ ] README.md with version info
   - [ ] Release notes prepared

3. **Commit Changes**
   ```bash
   git add CHANGELOG.md README.md
   git commit -m "chore: Release version 1.0.0"
   git push origin releases/1.0.0
   ```

4. **Create PR on GitHub**
   - Title: `Release: Version 1.0.0`
   - Description: Include changelog
   - Wait for ruleset enforcement

5. **Review & Merge**
   - Review your own changes
   - Approve PR
   - Merge to main

6. **Create GitHub Release**
   - Tag: `v1.0.0`
   - Release notes from CHANGELOG
   - Publish

7. **Clean Up**
   ```bash
   git checkout main
   git pull origin main
   git branch -d releases/1.0.0
   git push origin --delete releases/1.0.0
   ```

## Hotfix Releases

For critical patch fixes:

```bash
# Create hotfix from main (not a release branch)
git checkout main
git checkout -b hotfix/1.0.1

# Fix the issue
# Update CHANGELOG
git add .
git commit -m "fix: Critical issue in week 5"
git push origin hotfix/1.0.1

# Create PR → hotfix/1.0.1 → main
# After merge, create release tag v1.0.1
```

## Frequently Asked Questions

**Q: Can I update a release branch after it's created?**  
A: Yes, but only through PR workflow thanks to the ruleset.

**Q: Do I need a separate branch for each patch?**  
A: Yes, following the pattern `releases/1.0.1`, `releases/1.0.2`, etc.

**Q: Can I merge releases back to main?**  
A: They merge to main via PR, then you create GitHub Release tags.

**Q: What if I need to fix something in a released version?**  
A: Create a new release branch: `releases/1.0.1` with the fix.

---

**See also:**
- [RELEASE.md](RELEASE.md) - Complete release process guide
- [BRANCH_PROTECTION_SETUP.md](BRANCH_PROTECTION_SETUP.md) - Main branch ruleset setup
