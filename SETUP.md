# GitHub Repository Setup Guide

This document provides step-by-step instructions for converting your AI for Product Owner curriculum into a full GitHub repository with GitHub Pages deployment.

## What's Been Set Up

✅ **Complete GitHub Pages Website**
- Professional homepage with course overview
- 7 phase pages with week breakdowns
- Responsive design that works on mobile, tablet, and desktop
- Modern styling with CSS custom properties

✅ **Professional README.md**
- Course overview and learning outcomes
- Complete curriculum structure
- Links to all resources
- Contributing guidelines
- License information

✅ **GitHub Pages Configuration**
- `_config.yml` for Jekyll build settings
- Proper baseurl configuration
- SEO and metadata setup

✅ **Deployment Guide**
- Step-by-step instructions
- Local development setup
- Troubleshooting guide
- Customization instructions

✅ **Project Structure**
- Website directory with HTML pages
- Assets folder with CSS styling
- Curriculum, labs, and assessments properly organized
- Git configuration with .gitignore

## Quick Start - Deploy Your Course (5 minutes)

### 1. Push to GitHub

```bash
# If not already a git repository
git init
git add .
git commit -m "Initial commit: AI for Product Owner course"

# Create a new repository on GitHub at github.com/new
# Then add remote and push
git remote add origin https://github.com/YOUR_USERNAME/AI-for-Product-Owner.git
git branch -M main
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repository: `https://github.com/YOUR_USERNAME/AI-for-Product-Owner`
2. Click **Settings** (top right)
3. Click **Pages** (left sidebar)
4. Under "Source":
   - Select **Deploy from a branch**
   - Choose **main** branch
   - Select **/root** folder
5. Click **Save**

### 3. Wait and Visit Your Site

- GitHub will build your site (takes 1-2 minutes)
- Your site will be at: `https://YOUR_USERNAME.github.io/AI-for-Product-Owner/`
- Check the Actions tab to see build status

## Repository Files Overview

### Core Files
- `README.md` - Main repository documentation
- `LICENSE` - Creative Commons Attribution 4.0
- `CODE_OF_CONDUCT.md` - Community standards
- `CONTRIBUTING.md` - Contribution guidelines
- `DEPLOYMENT.md` - GitHub Pages setup guide (created)
- `.gitignore` - Git configuration (created)
- `_config.yml` - Jekyll/GitHub Pages config (created)

### Website Files
- `website/index.html` - Homepage with course overview
- `website/phase-1.html` through `website/phase-7.html` - Phase pages
- `website/assets/style.css` - Website styling

### Content Directories
- `curriculum/phase-*/` - Course content (20 weeks)
- `labs/` - Templates and tools
- `assessments/` - Certification exam

## Customization Options

### Change Your Site Title
Edit `website/index.html`:
```html
<div class="logo">🤖 Your Title Here</div>
```

### Change Colors
Edit `website/assets/style.css` in the `:root` section:
```css
:root {
  --primary-color: #your_color;
  --secondary-color: #your_color;
}
```

### Add Your Information
Edit `README.md`:
- Update author name
- Add your contact information
- Customize links

### Use a Custom Domain
1. Buy a domain
2. Add DNS records pointing to GitHub Pages
3. Go to Settings → Pages → Custom domain

## Before Going Live

### Checklist

- [ ] Course content is complete in markdown files
- [ ] Links in HTML pages point to correct markdown files
- [ ] All phase pages have been reviewed
- [ ] README.md contains accurate information
- [ ] Contributing guidelines are clear
- [ ] Code of Conduct reflects your values
- [ ] License is appropriate for your content

### Content Verification

1. Check all curriculum links work:
   - Visit `website/phase-1.html` → click lesson links
   - Verify they point to correct markdown files
   
2. Test responsive design:
   - View on desktop, tablet, and mobile
   - Test all navigation
   
3. Check for dead links:
   - Verify all GitHub links work
   - Test lab template links

## Managing Your Course

### Adding New Content

1. **Add a new lesson**:
   - Create markdown file: `curriculum/phase-1/week-01-new-lesson.md`
   - Add link to `website/phase-1.html`
   - Commit and push

2. **Add a new template**:
   - Create markdown file: `labs/new-template.md`
   - Add link to `website/index.html` in Labs section
   - Commit and push

3. **Update the website**:
   - Edit HTML or CSS files
   - Commit and push
   - Site updates automatically

### Managing Contributors

1. Set up collaboration:
   - Go to Settings → Collaborators
   - Add team members
   
2. Enable branch protection:
   - Go to Settings → Branches
   - Add rule for `main` branch
   - Require pull request reviews

3. Template pull requests:
   - Create `.github/pull_request_template.md`
   - Contributors use template for consistency

## Analytics & Monitoring

### GitHub Insights
- Go to Insights → Traffic
- See page views and referrers
- Monitor course popularity

### Google Analytics (Optional)
Add to `website/index.html` in `<head>`:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_ID');
</script>
```

## GitHub Features to Explore

### Discussions
Enable to allow community discussions:
- Settings → General → Discussions → Enable

### Wiki
Create documentation:
- Create wiki for FAQs
- Add troubleshooting guides

### Releases
Tag versions:
```bash
git tag -a v1.0 -m "Version 1.0 - Initial Release"
git push origin v1.0
```

### GitHub Pages Custom Theme
Optional: Switch to a built-in Jekyll theme in `_config.yml`:
```yaml
theme: jekyll-theme-midnight  # Options: minimal, time-machine, etc.
```

## Promoting Your Course

### Share Your Course
- Add link to GitHub profile README
- Share on social media
- Link from your personal website
- Submit to course directories

### GitHub Community
- Add topics: `ai` `product-management` `education` `curriculum`
- Create releases for major updates
- Write release notes

### README Badges
Already included in README.md:
- License badge (CC BY 4.0)
- Live site badge
- Add more: [Shields.io](https://shields.io)

## Troubleshooting

### Site Not Published
1. Check Settings → Pages
2. Verify branch is `main` and folder is `/root`
3. Check Actions tab for build errors
4. Clear browser cache (Ctrl+Shift+R)

### Links Not Working
1. Check relative paths in HTML
2. Verify markdown files exist
3. Test from root: `/AI-for-Product-Owner/path/to/file`

### Styles Not Loading
1. Verify `website/assets/style.css` exists
2. Check HTML for correct path: `assets/style.css`
3. Clear browser cache

## Next Steps

1. **Deploy**: Follow the Quick Start guide above
2. **Customize**: Update colors, text, and branding
3. **Share**: Spread the word about your course
4. **Engage**: Enable discussions for community interaction
5. **Iterate**: Update content based on feedback

## Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com)
- [GitHub Discussions Guide](https://docs.github.com/en/discussions)
- [GitHub Actions for CI/CD](https://docs.github.com/en/actions)

## Support

For help with:
- **GitHub Pages**: See DEPLOYMENT.md
- **Contributing**: See CONTRIBUTING.md
- **Community Standards**: See CODE_OF_CONDUCT.md

---

**Your AI for Product Owner course is ready to change the world!** 🚀

Start with the Quick Start section above and you'll have your course live in minutes.
