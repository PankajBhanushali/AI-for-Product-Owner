# GitHub Branch Protection Setup (Using Rulesets)

To enforce the pull request workflow and prevent direct commits to `main`, you need to configure GitHub Rulesets. This guide walks you through the setup using GitHub's modern Rulesets feature.

## Steps to Enable Branch Protection via Rulesets

### 1. Go to Repository Settings
1. Navigate to your repository on GitHub: `https://github.com/PankajBhanushali/AI-for-Product-Owner`
2. Click the **Settings** tab (top right)

### 2. Access Rulesets
1. In the left sidebar, click **Rules**
2. Under "Rulesets", click **New ruleset** → **New branch ruleset**

### 3. Configure the Ruleset

#### Step 1: Basic Information
- **Ruleset Name**: `GitHub Branch Protection Rules` (or similar)
- **Enforcement status**: Keep as default (Active)
- **Bypass list**: Leave empty (no exceptions)

#### Step 2: Target Branches
- **Branch targeting criteria**: Select `Default`
  - This will target your `main` branch (default branch)

#### Step 3: Rules Configuration

Enable the following rules:

##### ✅ **Restrict Updates**
- Only allow users with bypass permission to update matching refs
- This prevents direct pushes to `main`

##### ✅ **Restrict Deletions**
- Only allow users with bypass permissions to delete matching refs
- Prevents accidental deletion of main branch

##### ✅ **Block Force Pushes**
- Prevent users with push access from force pushing to refs
- Ensures commit history integrity

##### ✅ **Require a Pull Request Before Merging**
- Required approvals: `1`
- **Check options:**
  - ✓ Dismiss stale pull request approvals when new commits are pushed
  - ✓ Require review from Code Owners (if you have CODEOWNERS file)
  - ✓ Require approval of the most recent reviewable push
  - ✓ Require conversation resolution before merging

##### ✅ **Require Linear History** (optional but recommended)
- Prevent merge commits from being pushed to matching refs
- Keeps commit history clean and organized

##### ✅ **Require Status Checks to Pass** (optional)
- Leave empty if you don't have CI/CD pipelines
- Add checks if you set up automated testing

### 4. Save the Ruleset
Click **Create** button to save your ruleset

## Expected Behavior After Setup

Once the ruleset is enabled:

❌ **Cannot do:**
- Push directly to `main` branch
- Force push to `main`
- Update/modify commits already on `main` without PR
- Delete the `main` branch
- Merge PRs without approval

✅ **Can do:**
- Create feature branches
- Push to feature branches
- Create pull requests
- Merge PRs after approval

## What Contributors Will Experience

When contributors try to push to `main`, they'll get:
```
remote: error: GH006: Protected branch update failed for refs/heads/main.
remote: error: At least 1 approving review is required by reviewers with write access.
```

This error message directs them to create a pull request instead.

## Reviewing & Merging PRs

When a PR is created:

1. **Review the PR**
   - Check the changes
   - Leave comments if needed
   - Request changes if necessary

2. **Approve the PR**
   - Click the "Review changes" button
   - Select "Approve"
   - Add any comments

3. **Merge the PR**
   - Once approved, click "Merge pull request"
   - Choose merge strategy (squash, merge, rebase)
   - Confirm

## Best Practices

1. **Always review code** before merging
2. **Leave constructive feedback** if changes are needed
3. **Test changes locally** when possible
4. **Use meaningful commit messages** in merge commits
5. **Close related issues** by referencing them in PRs

## Related Documentation

- [GitHub: Creating branch rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/creating-rulesets-in-your-repository)
- [GitHub: Available rules for rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets)
- [GitHub: About rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)

---

Once this is set up, all contributions to your project will follow the PR workflow! 🎉
