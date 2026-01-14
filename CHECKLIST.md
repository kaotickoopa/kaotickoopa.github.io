# Deployment & Customization Checklist

## Pre-Deployment Checklist

### Repository Setup
- [ ] Fork or create repository named `username.github.io`
- [ ] Clone repository locally
- [ ] Install Ruby (2.7 or higher)
- [ ] Install Bundler: `gem install bundler`
- [ ] Run `bundle install`

### Local Testing
- [ ] Run `bundle exec jekyll serve`
- [ ] Visit `http://localhost:4000`
- [ ] Verify all pages load
- [ ] Check responsive design (test mobile view)
- [ ] Test navigation links
- [ ] Verify CSS styling

### Configuration
- [ ] Edit `_config.yml` with your details:
  - [ ] `title`: Your name or brand
  - [ ] `tagline`: Professional tagline
  - [ ] `description`: Brief description
  - [ ] `url`: Your GitHub Pages URL
  - [ ] `author.name`: Your full name
  - [ ] `author.email`: Your email
  - [ ] `author.github`: GitHub username
  - [ ] `author.linkedin`: LinkedIn username
  - [ ] `author.twitter`: Twitter handle

### Content Updates
- [ ] Update homepage (`index.md`)
  - [ ] Change hero title
  - [ ] Update hero subtitle
  - [ ] Modify hero description
  - [ ] Edit featured projects
  - [ ] Update skills sections
- [ ] Update about page (`about.md`)
  - [ ] Add your bio
  - [ ] Update technical expertise
  - [ ] Customize philosophy section
- [ ] Remove or update sample blog posts
- [ ] Remove or update sample projects

### Design Customization (Optional)
- [ ] Customize colors in `assets/css/style.css`
  - [ ] `--primary-color`
  - [ ] `--secondary-color`
  - [ ] `--accent-color`
- [ ] Update fonts if desired
- [ ] Adjust spacing/padding as needed

## GitHub Pages Setup

### Enable GitHub Pages
- [ ] Go to repository Settings
- [ ] Navigate to Pages section
- [ ] Set Source to `main` branch
- [ ] Set folder to `/ (root)`
- [ ] Click Save

### Initial Push
- [ ] Stage all files: `git add .`
- [ ] Commit: `git commit -m "Initial commit: Jekyll portfolio"`
- [ ] Push: `git push origin main`
- [ ] Wait 1-2 minutes for deployment
- [ ] Check Actions tab for successful build
- [ ] Visit your site: `https://username.github.io`

### Verify Deployment
- [ ] Check homepage loads
- [ ] Verify all pages are accessible
- [ ] Test navigation links
- [ ] Check mobile responsiveness
- [ ] Verify CSS loaded correctly
- [ ] Test contact links

## Content Management

### Add Your Projects
For each project:
- [ ] Create file in `_projects/`
- [ ] Use naming: `NN-slug.md`
- [ ] Fill in project details:
  - [ ] Title
  - [ ] Subtitle
  - [ ] Technologies
  - [ ] Role
  - [ ] GitHub/Live link
  - [ ] Description
- [ ] Push to GitHub

### Write Blog Posts
For each post:
- [ ] Create file in `_posts/`
- [ ] Use naming: `YYYY-MM-DD-slug.md`
- [ ] Add front matter:
  - [ ] Title
  - [ ] Date
  - [ ] Author
  - [ ] Tags
- [ ] Write content
- [ ] Push to GitHub

### Create Additional Pages
For new pages:
- [ ] Create `.md` file in root
- [ ] Add front matter with unique URL
- [ ] Add navigation link to navbar (`_includes/navbar.html`)
- [ ] Update footer if needed
- [ ] Push to GitHub

## Custom Domain Setup (Optional)

### Register Domain
- [ ] Purchase domain from registrar
- [ ] Note registrar details

### Configure DNS
- [ ] Add CNAME record (or A records)
- [ ] Point to `username.github.io`
- [ ] Allow time for DNS propagation (24-48 hours)

### Update GitHub Pages
- [ ] Repository Settings → Pages
- [ ] Enter custom domain
- [ ] Click Save
- [ ] Enable HTTPS (automatic after DNS setup)

## Analytics Setup (Optional)

### Google Analytics
- [ ] Create Google Analytics account
- [ ] Get Measurement ID
- [ ] Add to `_config.yml`:
  ```yaml
  google_analytics_id: G-XXXXXXXXXX
  ```

### Monitor Traffic
- [ ] Check GitHub Pages traffic (Settings → Pages)
- [ ] Review Google Analytics dashboard

## Maintenance Tasks

### Regular Updates
- [ ] Add new blog posts (at least monthly)
- [ ] Update projects as they're completed
- [ ] Review and update about section
- [ ] Check for Jekyll/plugin updates

### Monthly Checklist
- [ ] Write blog post or update content
- [ ] Check site loads correctly
- [ ] Verify all links work
- [ ] Review analytics (if using)

### Quarterly Checklist
- [ ] Update projects section
- [ ] Review and fix any issues
- [ ] Check for plugin updates: `bundle outdated`
- [ ] Test on multiple devices/browsers

## Troubleshooting Checklist

### Site Not Building
- [ ] Check Actions tab for errors
- [ ] Verify YAML syntax in `_config.yml`
- [ ] Check front matter in posts/projects
- [ ] Look for invalid Markdown syntax
- [ ] Run locally: `bundle exec jekyll build`

### Changes Not Appearing
- [ ] Wait 1-2 minutes for rebuild
- [ ] Clear browser cache (Ctrl+Shift+Delete)
- [ ] Check Actions for successful build
- [ ] Verify file names and dates
- [ ] Hard refresh (Ctrl+Shift+R)

### CSS/Images Not Loading
- [ ] Check browser console for errors
- [ ] Verify `baseurl` in `_config.yml`
- [ ] Check file paths in HTML/CSS
- [ ] Test locally first
- [ ] Hard refresh browser

### Links Not Working
- [ ] Verify file exists
- [ ] Check URL syntax
- [ ] Ensure relative paths correct
- [ ] Test with and without trailing slash

## Post-Launch Tasks

### Promotion
- [ ] Add link to GitHub profile
- [ ] Share on social media
- [ ] Include in email signature
- [ ] Add to job applications
- [ ] Submit to search engines (optional)

### SEO Optimization
- [ ] Verify sitemap at `/sitemap.xml`
- [ ] Check RSS feed at `/feed.xml`
- [ ] Submit sitemap to Google Search Console
- [ ] Monitor search performance
- [ ] Build backlinks

### Share & Connect
- [ ] Share portfolio on LinkedIn
- [ ] Tweet about your new site
- [ ] Share with professional network
- [ ] Update GitHub README
- [ ] Add to portfolio sites

## Documentation

### Update Your Notes
- [ ] Document your customizations
- [ ] Note any third-party services used
- [ ] Record domain information
- [ ] Store DNS records
- [ ] Keep backups

## Final Verification

Before considering the setup complete:
- [ ] Homepage loads and looks good
- [ ] All navigation links work
- [ ] Mobile view is responsive
- [ ] Blog posts display correctly
- [ ] Projects showcase properly
- [ ] About page is complete
- [ ] Contact links are functional
- [ ] Social links work
- [ ] No console errors
- [ ] SEO elements in place
- [ ] Site appears in search (may take time)

## Quick Reference Commands

```bash
# Install dependencies
bundle install

# Local development
bundle exec jekyll serve

# Build for production
bundle exec jekyll build

# Clean build
bundle exec jekyll clean && bundle exec jekyll build

# Check for outdated gems
bundle outdated

# Update gems
bundle update

# Git commands
git add .
git commit -m "message"
git push origin main
```

## Important Files to Remember

- `_config.yml` - Main configuration
- `_includes/navbar.html` - Navigation menu
- `_includes/footer.html` - Footer content
- `assets/css/style.css` - All styling
- `index.md` - Homepage
- `about.md` - About page
- `README.md` - Documentation

## Support Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Help](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)
- [YAML Reference](https://yaml.org/spec/)

---

## Status Tracking

Use this space to track your progress:

```
Date Started: _______________
Date Completed: _______________

Pages Created: ___/5
Blog Posts Added: ___/3+
Projects Added: ___/3+
Custom Domain: [ ] Yes [ ] No
Analytics Setup: [ ] Yes [ ] No
Site Live: [ ] Yes [ ] No
```

**Good luck! Your portfolio is ready to go! 🚀**
