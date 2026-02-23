# GitHub Pages Deployment Guide

## Overview

This course is designed to be deployed as a GitHub Pages site using custom HTML and CSS. The website serves as a portal to the curriculum, labs, assessments, and resources.

## Deployment Steps

### Step 1: Fork/Clone the Repository

```bash
# Clone the repository
git clone https://github.com/PankajBhanushali/AI-for-Product-Owner.git
cd AI-for-Product-Owner

# Or fork on GitHub and clone your fork
git clone https://github.com/YOUR_USERNAME/AI-for-Product-Owner.git
```

### Step 2: Enable GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under "Source":
   - Select **Deploy from a branch**
   - Choose **main** branch
   - Select **/root** folder
4. Click **Save**

Your site will be published at: `https://YOUR_USERNAME.github.io/AI-for-Product-Owner/`

### Step 3: Verify Deployment

1. Wait for the GitHub Actions workflow to complete (check the Actions tab)
2. Visit your GitHub Pages URL
3. You should see the homepage with the course overview

## Directory Structure

The website is organized as follows:

```
website/
├── index.html              # Main homepage
├── phase-1.html           # Phase 1 overview
├── phase-2.html           # Phase 2 overview
├── phase-3.html           # Phase 3 overview
├── phase-4.html           # Phase 4 overview
├── phase-5.html           # Phase 5 overview
├── phase-6.html           # Phase 6 overview
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
