# Release Guidelines

This document outlines the release process and versioning strategy for the AI for Product Owner project.

## Versioning Strategy

We follow **Semantic Versioning** (SemVer): `MAJOR.MINOR.PATCH`

- **MAJOR**: Breaking changes or significant new curriculum phases
- **MINOR**: New content additions, improvements, new weeks
- **PATCH**: Bug fixes, corrections, documentation updates

Examples:
- `1.0.0` - First stable release of complete curriculum
- `1.1.0` - Added new weeks or phase content
- `1.0.1` - Bug fix or typo correction
- `2.0.0` - Major restructure or breaking changes

## Release Process

### Step 1: Prepare Release Branch

```bash
# Create a release branch from main
git checkout main
git pull origin main
git checkout -b releases/1.0.0

# OR if working on a patch
git checkout -b releases/1.0.1
```

### Step 2: Update Version Numbers

Update version information in relevant files:
- `README.md` - Update version references
- `website/index.html` - Update release info if visible
- Any documentation mentioning version

### Step 3: Update CHANGELOG.md

Add an entry for the new release:

```markdown
## [1.0.0] - 2026-02-24

### Added
- Complete 20-week AI curriculum
- 7 phases with comprehensive content
- Website with organized phase structure
- Labs and templates for practitioners

### Changed
- Restructured website into phase-wise folders
- Updated all internal links for GitHub Pages deployment

### Fixed
- CSS path issues in phase pages
- Curriculum link navigation

### Security
- Implemented branch protection for main branch
- Established PR review workflow
```

### Step 4: Commit Changes

```bash
# Add release files
git add CHANGELOG.md README.md

# Commit with clear message
git commit -m "chore: Release version 1.0.0"
```

### Step 5: Create Pull Request

```bash
# Push release branch
git push origin releases/1.0.0
```

Then on GitHub:
1. Create a Pull Request from `releases/1.0.0` → `main`
2. Title: `Release: Version 1.0.0`
3. Description: Include changelog summary
4. Wait for review/approval
5. Merge to main

### Step 6: Create GitHub Release

After merging to main:

1. Go to **Releases** tab on GitHub
2. Click **Draft a new release**
3. Fill in:
   - **Tag version**: `v1.0.0`
   - **Release title**: `Release 1.0.0 - AI Curriculum Complete`
   - **Description**: Copy from CHANGELOG.md
4. Check **This is a pre-release** if applicable
5. Click **Publish release**

### Step 7: Clean Up

```bash
# Delete the release branch locally
git branch -d releases/1.0.0

# Delete on remote
git push origin --delete releases/1.0.0
```

## Branch Protection for Release Branches

Release branches should follow the same PR workflow as main:
- No direct commits
- Require PR review before merging
- Maintain clean history

To set up ruleset for release branches, use pattern: `releases/**`

## Release Types

### Major Release (e.g., 1.0.0)
- New major phases or curriculum restructure
- Breaking changes to existing content
- Significant new features

**Checklist:**
- [ ] All tests pass
- [ ] Documentation updated
- [ ] CHANGELOG complete
- [ ] Version numbers updated
- [ ] Release notes prepared

### Minor Release (e.g., 1.1.0)
- New week or content additions
- Improvements to existing content
- Non-breaking new features

**Checklist:**
- [ ] New content reviewed
- [ ] Links tested
- [ ] CHANGELOG updated
- [ ] Version bumped

### Patch Release (e.g., 1.0.1)
- Bug fixes
- Typo corrections
- Minor documentation updates

**Checklist:**
- [ ] Bug confirmed fixed
- [ ] No regression
- [ ] CHANGELOG entry added

## Release Schedule

- **Planned releases**: Announced in advance
- **Patch releases**: As needed for fixes
- **Major releases**: Quarterly or as milestones reached

## Communication

When releasing:

1. **Update README**: Add version info
2. **GitHub Release Page**: Full release notes
3. **CHANGELOG.md**: Detailed changes
4. **Issues/Discussions**: Announce to community

## Rolling Back a Release

If a release has critical issues:

```bash
# Create a hotfix branch from main
git checkout main
git checkout -b releases/1.0.1

# Fix the issue
# Follow release process above

# The new patch version becomes the stable release
```

## Examples

### Example 1: Release 1.0.0

```bash
git checkout main
git checkout -b releases/1.0.0

# Update version files
# Update CHANGELOG.md
git add .
git commit -m "chore: Release version 1.0.0"
git push origin releases/1.0.0

# Create PR, review, merge
# Create GitHub release with tag v1.0.0
```

### Example 2: Patch Release 1.0.1

```bash
git checkout main
git checkout -b releases/1.0.1

# Fix bug
# Update CHANGELOG.md
git add .
git commit -m "fix: Critical bug in week 5 content"
git push origin releases/1.0.1

# Create PR, review, merge
# Create GitHub release with tag v1.0.1
```

## Files to Update for Each Release

- [ ] `CHANGELOG.md` - Document all changes
- [ ] `README.md` - Update version reference
- [ ] Version files in project
- [ ] Release notes/documentation
- [ ] Any package.json or version manifests

## Continuous Delivery

This release process supports:
- ✅ Controlled releases
- ✅ Community collaboration
- ✅ Clear change tracking
- ✅ Easy rollback
- ✅ Semantic versioning
- ✅ Professional release management

---

**Questions?** See CONTRIBUTING.md for general guidelines or create an issue to discuss release plans.
