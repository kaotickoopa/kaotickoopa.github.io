---
layout: post
title: "Getting Started with Jekyll and GitHub Pages"
date: 2024-10-15
author: "Mason"
tags: ["Jekyll", "GitHub Pages", "Web Development", "Tutorial"]
---

Building a professional portfolio website doesn't have to be complicated. In this post, I'll show you how to create a beautiful portfolio using Jekyll and host it for free on GitHub Pages.

## What is Jekyll?

Jekyll is a static site generator that transforms plain text files into a complete website. It's perfect for blogs, portfolios, and documentation sites.

### Why Jekyll?

- **Fast**: No database queries, just pure HTML
- **Secure**: No server-side vulnerabilities
- **Free Hosting**: Perfect for GitHub Pages
- **Version Control**: Track your site in Git
- **Flexible**: Use themes or create custom designs

## Getting Started

### Prerequisites
- Ruby installed on your system
- Git knowledge
- Text editor

### Installation

```bash
# Install Jekyll and Bundler
gem install jekyll bundler

# Create a new site
jekyll new my-portfolio

# Navigate to your site
cd my-portfolio

# Start the development server
bundle exec jekyll serve
```

Visit `http://localhost:4000` to see your site!

## Project Structure

```
.
├── _config.yml          # Site configuration
├── _includes/           # Reusable components
├── _layouts/            # Template layouts
├── _posts/              # Blog posts
├── _projects/           # Project pages
├── assets/              # CSS, JS, images
├── index.md             # Home page
├── about.md             # About page
└── Gemfile              # Ruby dependencies
```

## Key Files Explained

### _config.yml
Configuration file for your site. Set your title, author, and plugins here.

```yaml
title: "My Portfolio"
author: "Your Name"
theme: minima

plugins:
  - jekyll-feed
  - jekyll-sitemap
  - jekyll-seo-tag
```

### Front Matter
Every markdown file starts with YAML front matter defining metadata:

```markdown
---
layout: post
title: "My Blog Post"
date: 2024-10-15
tags: ["jekyll", "tutorial"]
---

Your content here...
```

### Layouts
Reusable HTML templates in `_layouts/`:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```

## Writing Content

### Blog Posts
Create files in `_posts/` with the format: `YYYY-MM-DD-title.md`

```markdown
---
layout: post
title: "My First Post"
date: 2024-10-15
---

# Welcome

This is my first blog post!
```

### Project Pages
Use a custom collection in `_projects/`:

```markdown
---
layout: project
title: "My Project"
technologies: ["React", "Node.js"]
---

## Project Description
...
```

## Customization

### Creating Custom Layouts
Create `_layouts/custom.html`:

```html
---
layout: default
---

<div class="custom-wrapper">
  {{ content }}
</div>
```

### Adding CSS
Create `assets/css/style.css`:

```css
:root {
  --primary-color: #2c3e50;
  --text-color: #333;
}

body {
  color: var(--text-color);
}
```

### Using Liquid Tags
Jekyll uses Liquid templating for dynamic content:

```html
<!-- Loop through posts -->
{% for post in site.posts %}
  <article>
    <h2>{{ post.title }}</h2>
    <p>{{ post.excerpt }}</p>
  </article>
{% endfor %}

<!-- Conditional -->
{% if page.author %}
  <p>By {{ page.author }}</p>
{% endif %}
```

## Hosting on GitHub Pages

### Setup

1. Create repository named `username.github.io`
2. Push your Jekyll site to main branch
3. GitHub automatically builds and serves your site
4. Visit `https://username.github.io`

### GitHub Actions (Optional)
For more control, use GitHub Actions to build Jekyll:

```yaml
name: Build and Deploy

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: ruby/setup-ruby@v1
      - run: bundle install
      - run: bundle exec jekyll build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./_site
```

## Performance Tips

1. **Minify CSS/JS**: Reduce file sizes
2. **Optimize Images**: Use responsive images
3. **Lazy Loading**: Load images on demand
4. **Caching**: Configure GitHub Pages cache

## SEO Optimization

Use the jekyll-seo-tag plugin:

```html
{% seo %}
```

Set metadata in `_config.yml`:

```yaml
title: "My Portfolio"
description: "Software Engineer & Developer"
author:
  name: "Your Name"
  email: "your@email.com"
```

## Deploying Custom Domains

1. Add `CNAME` file to root:
   ```
   myportfolio.com
   ```

2. Update DNS records to point to GitHub Pages

3. Enable HTTPS in repository settings

## Troubleshooting

### Site not building?
- Check Jekyll version in `Gemfile.lock`
- Verify YAML syntax in front matter
- Check `_config.yml` for errors

### Changes not showing?
- Clear browser cache
- Rebuild locally: `bundle exec jekyll build`
- Wait for GitHub to rebuild

## Resources

- [Jekyll Documentation](https://jekyllrb.com/)
- [GitHub Pages Guide](https://pages.github.com/)
- [Liquid Templating](https://shopify.github.io/liquid/)
- [Jekyll Themes](http://jekyllthemes.org/)

## Conclusion

Jekyll makes it easy to build a professional portfolio without dealing with complex backends. Combined with GitHub Pages' free hosting, you have a powerful platform for showcasing your work.

Start building your portfolio today and take control of your online presence!

---

Questions? Check out the [Jekyll documentation](https://jekyllrb.com/) or leave a comment below!
