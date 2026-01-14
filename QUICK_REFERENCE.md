# Quick Reference Guide

A quick reference for managing this Jekyll portfolio.

## Common Tasks

### Adding a Blog Post

1. Create file: `_posts/YYYY-MM-DD-slug.md`
2. Add front matter:
   ```yaml
   ---
   layout: post
   title: "Post Title"
   date: 2024-11-05
   author: "Your Name"
   tags: ["tag1", "tag2"]
   ---
   ```
3. Write content in Markdown
4. Push to GitHub

**Example**:
```bash
# _posts/2024-11-05-my-post.md
---
layout: post
title: "Getting Started with React"
date: 2024-11-05
author: "Mason"
tags: ["React", "JavaScript", "Tutorial"]
---

# Getting Started with React
...content...
```

### Adding a Project

1. Create file: `_projects/NN-slug.md` (NN = order number)
2. Add front matter:
   ```yaml
   ---
   layout: project
   title: "Project Name"
   slug: "project-slug"
   subtitle: "Brief description"
   date: 2024-11-01
   technologies: ["Tech1", "Tech2"]
   role: "Your Role"
   link: "https://github.com/..."
   ---
   ```
3. Write project description
4. Push to GitHub

### Adding a Page

1. Create file: `page-name.md` in root
2. Add front matter:
   ```yaml
   ---
   layout: page
   title: "Page Title"
   permalink: /page-slug/
   ---
   ```
3. Write content
4. Update navigation links

### Updating Configuration

Edit `_config.yml`:
- Site title, tagline, description
- Author information
- Social media links
- Theme settings

### Local Testing

```bash
# Install dependencies
bundle install

# Start server
bundle exec jekyll serve

# Visit http://localhost:4000

# Stop server
Ctrl+C
```

### Publishing Changes

```bash
# Check status
git status

# Stage changes
git add .

# Commit
git commit -m "Your message"

# Push
git push origin main
```

## File Structure Quick Reference

```
_config.yml          ← Site configuration
_includes/
  navbar.html        ← Navigation bar
  footer.html        ← Footer
_layouts/
  default.html       ← Base layout
  page.html
  post.html          ← Blog post layout
  project.html       ← Project layout
_posts/              ← Blog posts (Markdown)
_projects/           ← Projects showcase
assets/
  css/style.css      ← Main styles
  js/main.js         ← JavaScript
index.md             ← Home page
about.md             ← About page
blog.md              ← Blog listing
projects.md          ← Projects listing
Gemfile              ← Ruby dependencies
README.md            ← This file
```

## Front Matter Reference

### Post Front Matter
```yaml
---
layout: post
title: "Post Title"
date: 2024-11-05
author: "Author Name"
tags: ["tag1", "tag2", "tag3"]
---
```

### Project Front Matter
```yaml
---
layout: project
title: "Project Title"
slug: "unique-slug"
subtitle: "Short description"
date: 2024-11-01
technologies: ["React", "Node.js", "PostgreSQL"]
role: "Full-Stack Developer"
link: "https://github.com/username/repo"
---
```

### Page Front Matter
```yaml
---
layout: page
title: "Page Title"
permalink: /page-slug/
---
```

## Customization Quick Tips

### Change Colors
Edit `assets/css/style.css`:
```css
:root {
    --primary-color: #2c3e50;      /* Main color */
    --secondary-color: #3498db;    /* Accent color */
    --accent-color: #e74c3c;       /* Highlight color */
    /* ... more variables ... */
}
```

### Update Social Links
Edit `_config.yml`:
```yaml
author:
  name: "Your Name"
  email: "email@example.com"
  github: "github-username"
  linkedin: "linkedin-username"
  twitter: "twitter-handle"
```

### Change Homepage Content
Edit `index.md`:
- Update hero section
- Modify featured projects
- Edit skills list
- Change contact section

### Customize Navigation
Edit `_includes/navbar.html`:
```html
<li class="nav-item">
    <a href="/new-page/" class="nav-link">New Page</a>
</li>
```

## Markdown Cheat Sheet

```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*
~~Strikethrough~~

- Bullet list
  - Nested item

1. Numbered list
2. Another item

[Link text](https://example.com)
![Image alt](image.jpg)

> Blockquote
> Multiple lines

`Inline code`

\`\`\`javascript
// Code block
const hello = "world";
\`\`\`

| Column 1 | Column 2 |
|----------|----------|
| Cell 1   | Cell 2   |
```

## GitHub Pages Deployment

```bash
# Check deployment status
# Settings → Pages or Actions tab

# Changes publish automatically:
1. Edit files
2. Commit changes
3. Push to main/master
4. GitHub Actions builds and deploys
```

## Troubleshooting

### Posts not showing
- Check date is not in future
- Verify filename: `YYYY-MM-DD-slug.md`
- Check YAML front matter syntax

### CSS not updating
- Clear browser cache (Ctrl+Shift+Delete)
- Restart Jekyll server if local testing
- Check CSS syntax

### Changes not appearing
- Wait 1-2 minutes for GitHub Actions
- Check Actions tab for errors
- Verify files were committed

### Site not building
- Check `_config.yml` YAML syntax
- Verify front matter in posts
- View Actions tab for error details

## Useful Gems/Plugins

Already installed:
- `jekyll-feed` - RSS feed generation
- `jekyll-sitemap` - Sitemap generation
- `jekyll-seo-tag` - SEO optimization

## Resources

- [Jekyll Docs](https://jekyllrb.com/docs/)
- [GitHub Pages](https://pages.github.com/)
- [Markdown Guide](https://www.markdownguide.org/)
- [YAML Reference](https://yaml.org/spec/)

## Need Help?

1. Check Jekyll documentation
2. Review this guide
3. Check GitHub Actions for build errors
4. Search GitHub Issues for common problems

---

**Happy blogging and building! 🚀**
