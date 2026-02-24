# Deployment Configuration

This project uses GitHub Actions to automatically deploy to GitHub Pages for both production and staging environments.

## Dual Environment Setup

You now have two automatically deployed environments:

### Production (main branch)
```
https://pankajbhanushali.github.io/AI-for-Product-Owner/

Status: Live for all users
Branch: main
Auto-deploy: Yes
Deployment branch: main-pages
```

### Staging (dev branch)
```
https://pankajbhanushali.github.io/AI-for-Product-Owner-dev/

Status: For testing/previews
Branch: dev
Auto-deploy: Yes
Deployment branch: dev-pages
```

## Automatic Deployment Workflow

The GitHub Actions workflow (`.github/workflows/deploy.yml`) automatically:

1. **Watches** for pushes to `main` or `dev` branches
2. **Builds** the `website/` directory
3. **Deploys** to GitHub Pages
4. **Maps** branches:
   - `main` → `main-pages` → Production URL
   - `dev` → `dev-pages` → Staging URL

## Release Process with Two Environments

### Step 1: Create Release Branch from Dev
```bash
git checkout dev
git pull origin dev
git checkout -b releases/1.1.0

# Make content changes
git add .
git commit -m "Add Week 21 content for v1.1.0"
git push origin releases/1.1.0
```

### Step 2: Test in Staging
```bash
# Create PR: releases/1.1.0 → dev
# On GitHub:
#   1. Go to Pull Requests
#   2. Click "New Pull Request"
#   3. Select releases/1.1.0 → dev
#   4. Create PR and describe changes
#   5. Merge to dev
```

### Step 3: GitHub Actions Deploys to Staging
```
PR merged to dev
    ↓
GitHub Actions workflow triggered
    ↓
Builds website/ directory
    ↓
Pushes to dev-pages branch
    ↓
Deploy complete in ~1-2 minutes
    ↓
View at: https://pankajbhanushali.github.io/AI-for-Product-Owner-dev/
```

### Step 4: Review Changes in Staging
- Visit your staging URL above
- Test all the changes
- Ensure everything looks correct
- Share URL with team for review

### Step 5: Create PR to Production
```bash
# Create PR: dev → main
# On GitHub:
#   1. Go to Pull Requests
#   2. Click "New Pull Request"
#   3. Select dev → main
#   4. Add final notes
#   5. Merge to main
```

### Step 6: GitHub Actions Deploys to Production
```
PR merged to main
    ↓
GitHub Actions workflow triggered
    ↓
Builds website/ directory
    ↓
Pushes to main-pages branch
    ↓
Deploy complete in ~1-2 minutes
    ↓
Live at: https://pankajbhanushali.github.io/AI-for-Product-Owner/
    ↓
All users see new version
```

## Managing Both Environments

### Current Content Distribution

```
Week Content:

Development (local)
    ↓
Feature Branch (releases/1.1.0)
    ↓
Dev Branch (development environment)
    ↓
Staging URL: https://.../dev/
    ↓
Main Branch (production environment)
    ↓
Production URL: https://.../
```

### Multiple Release Branches

You can work on multiple versions simultaneously:

```
main-pages (v1.0.0 - LIVE for users)
  ↑
  └─ main branch

dev-pages (v1.1.0-beta - STAGING for testing)
  ↑
  └─ dev branch
      ↑
      ├─ releases/1.1.0 (in PR)
      ├─ releases/1.0.1 (hotfix branch)
      └─ feature/week-21 (new content)
```

## GitHub Pages Configuration

GitHub Pages is automatically configured through GitHub Actions.

### Settings to Verify

1. Go to **Settings → Pages**
2. You should see:
   - Source: **GitHub Actions** (configured)
   - Status: ✅ **Published** or **Publishing**

3. GitHub automatically creates:
   - `main-pages` branch (production)
   - `dev-pages` branch (staging)

## Monitoring Deployments

### View Deployment Status

1. Go to **Actions** tab
2. Look for "Deploy" workflow runs
3. See status:
   - ✅ **Success** = Deployed successfully
   - ❌ **Failed** = Check logs for errors
   - ⏳ **In progress** = Deployment running

### View All Deployments

1. Go to **Deployments** tab
2. See all environments:
   - github-pages (main-pages)
   - github-pages (dev-pages)
3. Click to view:
   - Deployment date/time
   - Commit that was deployed
   - Current status

### Revert Deployment

If something goes wrong:

1. Go to **Deployments**
2. Find the problematic deployment
3. Click "Re-run jobs"
4. Or manually push previous commit
5. GitHub Actions redeploys automatically

## Example Timeline

**Monday**
```
Production: v1.0.0 live
Staging: Same as production
```

**Tuesday-Wednesday**
```
Production: v1.0.0 (unchanged, users see this)
Staging: v1.1.0-beta (deploys automatically)
        Team tests at staging URL
        Reviews changes
        Approves PR
```

**Thursday**
```
Production: v1.1.0 (deployed, users see new version)
Staging: v1.1.0 (now matches production)
        Ready for next release cycle
```

## Directory Structure

The website is organized as follows:

```
website/
├── index.html
├── assets/
│   └── style.css
├── labs/
│   ├── ai-backlog-template.md
│   ├── ai-cost-calculator-guide.md
│   ├── ai-risk-register-template.md
│   └── prompt-test-matrix.md
├── phase-1/
│   ├── index.html
│   ├── week-01.html
│   ├── week-02.html
│   └── week-03.html
├── phase-2/ through phase-7/
│   └── (similar structure)
```

## Troubleshooting

### Deployment Failed

**Check the logs:**
1. Go to **Actions** tab
2. Click "Deploy" workflow
3. Click failed run
4. See error message

**Common issues:**
- File path errors (check `publish_dir: ./website`)
- Branch name typo (must be `main` or `dev`)
- Missing `github_token` (auto-configured)

### Website Not Updating

1. ✅ Check GitHub Actions completed successfully
2. ✅ Wait 1-2 minutes for propagation
3. ✅ Clear browser cache (Ctrl+Shift+Delete or Cmd+Shift+Delete)
4. ✅ Visit incognito/private window
5. ✅ Check correct URL (main vs dev)

### Want to Add Another Environment?

Add another branch to the workflow:

```yaml
on:
  push:
    branches: [main, dev, staging]  # Add new branch
```

Push to the new branch, GitHub Actions automatically deploys!

## Deployment Workflow Summary

```
Developer makes changes
    ↓
Create feature branch (git checkout -b feature/...)
    ↓
Push to feature branch
    ↓
Create PR → dev branch
    ↓
(GitHub Actions deploys to dev-pages if merging to dev)
    ↓
Test at staging URL
    ↓
Create PR → main branch
    ↓
(GitHub Actions deploys to main-pages if merging to main)
    ↓
Users see production version
```

## Configuration Files

- **GitHub Actions**: `.github/workflows/deploy.yml`
- **Website**: `website/` directory
- **GitHub Pages**: Automatic (via Actions)

## Security

- ✅ Uses GitHub's automatic `GITHUB_TOKEN`
- ✅ No manual secrets needed
- ✅ Protected by branch rulesets
- ✅ Only authorized merges trigger deploys
├── phase-7.html           # Phase 7 overview
└── assets/
    └── style.css          # Global styles
```

The curriculum content is linked from the website to the markdown files in the `/curriculum/` directory.

## Local Development

To test the site locally before deploying:

### Option 1: Using Python HTTP Server

```bash
cd website
python -m http.server 8000
```

Then visit `http://localhost:8000` in your browser.

### Option 2: Using Jekyll (if installed)

```bash
gem install bundler jekyll
bundle install
bundle exec jekyll serve
```

Then visit `http://localhost:4000` in your browser.

## Customization

### Change the Title

Edit `/website/index.html` and update the `<title>` tag and `<h1>` text.

### Change Colors

Edit `/website/assets/style.css` and modify the CSS custom properties in the `:root` section:

```css
:root {
  --primary-color: #1e40af;
  --secondary-color: #f59e0b;
  /* ... other colors ... */
}
```

### Update Navigation

Edit `/website/index.html` and `/website/phase-*.html` to update the navigation menu and links.

### Add New Pages

1. Create a new HTML file in `/website/` (e.g., `custom-page.html`)
2. Use the same header, footer, and styling as existing pages
3. Import the CSS: `<link rel="stylesheet" href="assets/style.css">`
4. Add link to header navigation if needed

## Content Management

The website links to markdown content files:

- **Curriculum**: Located in `/curriculum/phase-*/week-*.md`
- **Labs**: Located in `/labs/*.md`
- **Assessments**: Located in `/assessments/*.md`

These files are linked from the HTML pages but not directly served by GitHub Pages. Users can:
1. View them in the GitHub repository
2. Download and view locally
3. Copy content for their own use

## GitHub Actions

If you want automatic deployment:

1. GitHub Pages automatically deploys when you push to `main`
2. Check the Actions tab to see deployment status
3. Look for "pages build and deployment" workflow

## Troubleshooting

### Site not appearing

- Check that Pages is enabled in Settings
- Verify the source branch is set to `main` and folder is `/root`
- Wait a few minutes for GitHub to process the changes
- Check the Actions tab for build errors

### Styles not loading

- Verify the `assets/style.css` file path is correct
- Clear your browser cache and reload (Ctrl+Shift+R or Cmd+Shift+R)
- Check browser console for 404 errors

### Links broken

- Verify relative paths in HTML files match your directory structure
- Remember that GitHub Pages URLs include `/AI-for-Product-Owner/` in the path

## Custom Domain (Optional)

To use a custom domain:

1. Purchase a domain from a registrar
2. Update DNS records to point to GitHub Pages
3. Go to Settings → Pages → Custom domain
4. Enter your domain and click Save
5. GitHub will create a CNAME file

See [GitHub Pages documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site) for detailed instructions.

## Analytics (Optional)

To add Google Analytics or other tracking:

1. Add a Google Analytics tag in the `<head>` section of HTML files
2. Or use GitHub Insights for basic traffic stats

Example Google Analytics (add to `<head>`):

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=YOUR_GA_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'YOUR_GA_ID');
</script>
```

## Updating Content

To update course content:

1. Edit markdown files in `/curriculum/`, `/labs/`, or `/assessments/`
2. Update HTML files in `/website/` if needed
3. Commit and push changes
4. GitHub Pages automatically updates within minutes

## Contributing to the Course

For contributions:

1. See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines
2. Create a branch for your changes
3. Submit a pull request
4. Site updates automatically when merged

## Support

For questions about GitHub Pages deployment, see:
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Pages Troubleshooting](https://docs.github.com/en/pages/getting-started-with-github-pages/troubleshooting-java-lang-nullpointerexception-error-for-github-pages)

---

**Happy deploying!** 🚀

Your AI for Product Owner course is now live and ready for the world to learn from your curriculum.
