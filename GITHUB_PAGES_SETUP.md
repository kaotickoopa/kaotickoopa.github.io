# GitHub Pages Setup Guide

This guide walks you through setting up this Jekyll portfolio on GitHub Pages.

## Prerequisites

- GitHub account
- Git installed on your computer
- Basic knowledge of terminal/command line
- Ruby and Bundler (for local development)

## Step 1: Repository Setup

### Option A: Using the Correct Repository Name

1. Fork this repository or create a new repository named `username.github.io` (replace `username` with your GitHub username)
2. Clone it locally:
   ```bash
   git clone https://github.com/username/username.github.io.git
   cd username.github.io
   ```

### Option B: Using Any Repository Name

If you want to use a different repository name:
1. Create a new repository (e.g., `my-portfolio`)
2. In repository Settings → Pages → Source, select the branch and folder to deploy from
3. The site will be available at `https://username.github.io/my-portfolio/`
4. Update `_config.yml`:
   ```yaml
   baseurl: "/my-portfolio"
   url: "https://username.github.io"
   ```

## Step 2: Customize Configuration

Edit `_config.yml`:

```yaml
# Basic Info
title: "Your Name"
tagline: "Your Professional Tagline"
description: "A brief description of your portfolio"
url: "https://username.github.io"
baseurl: ""

# Author Information
author:
  name: "Your Full Name"
  email: "your-email@example.com"
  github: "your-github-username"
  linkedin: "your-linkedin-username"
  twitter: "your-twitter-handle"
```

## Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click "Settings" (gear icon)
3. Scroll to "Pages" in the left sidebar
4. Under "Build and deployment":
   - **Source**: Select "Deploy from a branch"
   - **Branch**: Select `main` (or `master`)
   - **Folder**: Select `/ (root)`
5. Click "Save"

## Step 4: Add Custom Domain (Optional)

1. Go to Settings → Pages
2. Under "Custom domain", enter your domain (e.g., `yourdomain.com`)
3. Click "Save"
4. Update your domain registrar's DNS records:
   - Add `CNAME` record pointing to `username.github.io`
   - Or add `A` records pointing to GitHub Pages IP addresses

GitHub will automatically enable HTTPS for your site.

## Step 5: Verify Deployment

1. Go to Settings → Pages
2. Look for "Your site is live at https://username.github.io"
3. Visit your site in a browser
4. GitHub Actions will automatically build and deploy your site

## Step 6: Local Development (Optional)

For local testing before pushing to GitHub:

```bash
# Install dependencies
bundle install

# Start local server
bundle exec jekyll serve

# Visit http://localhost:4000 in your browser
```

## Common GitHub Pages Issues

### Issue: Site not building

**Check the Actions tab**:
1. Go to repository → Actions
2. Look at recent workflow runs
3. Click on failed builds to see error messages

**Common causes**:
- YAML syntax errors in `_config.yml` or front matter
- Missing Gemfile or bundle issues
- Invalid Markdown syntax

### Issue: Changes not appearing

1. Wait 1-2 minutes for GitHub Actions to rebuild
2. Clear browser cache (Ctrl+Shift+Delete)
3. Check Actions tab to see if deployment succeeded

### Issue: CSS/Images not loading with custom domain

Make sure `_config.yml` has correct `baseurl`:
```yaml
url: "https://yourdomain.com"
baseurl: ""
```

## GitHub Actions Configuration

The site automatically builds with GitHub Actions. No configuration needed!

You can monitor builds in: **Actions** tab → **pages-build-deployment** workflow

## Protection Rules (Optional)

Protect your main branch:
1. Settings → Branches
2. Add rule for `main` branch
3. Enable "Require pull request reviews"
4. Enable "Include administrators"

## Monitoring & Analytics

### Add Google Analytics

1. Create Google Analytics account
2. Get your Measurement ID
3. Add to `_config.yml`:
   ```yaml
   google_analytics_id: G-XXXXXXXXXX
   ```

### Monitor Traffic

GitHub Pages provides basic traffic statistics:
1. Settings → Pages
2. Scroll down to see view stats

## Troubleshooting Checklist

- [ ] Repository name is `username.github.io`
- [ ] Settings → Pages shows your site URL
- [ ] `_config.yml` has valid YAML syntax
- [ ] No syntax errors in front matter
- [ ] Correct baseurl in `_config.yml`
- [ ] Actions workflow completed successfully
- [ ] Browser cache cleared
- [ ] DNS records configured correctly (if using custom domain)

## Next Steps

1. **Add your content**:
   - Update `_config.yml` with your info
   - Edit homepage in `index.md`
   - Create blog posts in `_posts/`
   - Add projects in `_projects/`

2. **Customize design**:
   - Edit CSS in `assets/css/style.css`
   - Update colors in CSS variables
   - Modify layouts in `_layouts/`

3. **Share your portfolio**:
   - Add link to GitHub profile
   - Share on social media
   - Use in job applications

## Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Markdown Guide](https://www.markdownguide.org/)

## Support

If you encounter issues:

1. Check GitHub Actions for error messages
2. Review Jekyll logs: `bundle exec jekyll serve --verbose`
3. Validate YAML: Use an online YAML validator
4. Check [Jekyll Documentation](https://jekyllrb.com/docs/)

---

**Your portfolio is now live! Keep it updated with your latest projects and blog posts.**
