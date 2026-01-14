# Site Map & Navigation

## Website Structure

```
🏠 Home (index.md)
├── Hero Section
│   ├── Title & Subtitle
│   ├── Description
│   └── CTA Buttons → Projects & About
├── Featured Projects
│   ├── Project Cards
│   └── View Details Links → /projects/[slug]
├── About Section
│   └── Brief Bio
├── Skills Section
│   ├── Frontend Skills
│   ├── Backend Skills
│   └── Tools & DevOps
├── Latest Blog Posts
│   ├── Post Preview 1
│   ├── Post Preview 2
│   ├── Post Preview 3
│   └── View All → /blog
└── Contact Section
    ├── GitHub
    ├── LinkedIn
    ├── Twitter
    └── Email

📄 Pages
├── About (/about)
│   ├── Personal Statement
│   ├── Background
│   ├── Expertise
│   ├── Philosophy
│   └── Contact Info
├── Blog (/blog)
│   ├── Post Listings (Grid)
│   ├── Post Cards
│   │   ├── Title
│   │   ├── Date
│   │   ├── Excerpt
│   │   └── Tags
│   └── Filter by Tag
├── Projects (/projects)
│   ├── Project Listings
│   ├── Project Items
│   │   ├── Title & Subtitle
│   │   ├── Tech Stack
│   │   ├── Role
│   │   └── Links
│   └── View Details
└── Individual Project Pages (/projects/[slug])
    ├── Project Title
    ├── Project Metadata
    ├── Full Description
    ├── Technical Details
    ├── Live Link
    └── Repository Link

📝 Blog System
├── Post Listings (/blog)
├── Individual Posts (/blog/YYYY/MM/DD/slug)
│   ├── Post Title
│   ├── Date & Author
│   ├── Tags
│   ├── Full Content
│   └── Navigation
│       ├── Previous Post
│       └── Next Post
└── Tag Pages (/blog/tags/[tag])
    └── Posts with specific tag

```

## URL Structure

```
/                           → Home page
/about                      → About page
/blog                       → Blog listing
/blog/2024/11/05/post-title → Blog post
/blog/tags/react            → Posts tagged with "react"
/projects                   → Projects listing
/projects/peercafe          → Project detail
/feed.xml                   → RSS feed
/sitemap.xml                → XML sitemap
```

## Navigation Paths

### From Homepage
- **View My Projects** → Anchor to projects section → /projects
- **Learn More** → Anchor to about section → /about
- **View All Posts** → /blog
- **Social Links** → External (GitHub, LinkedIn, etc.)

### From Navigation Bar
- **Home** → /
- **Projects** → /#projects
- **Blog** → /blog
- **About** → /#about
- **Contact** → /#contact

### From Footer
- **Home** → /
- **Projects** → /#projects
- **Blog** → /blog
- **About** → /#about
- **GitHub** → External
- **LinkedIn** → External
- **Twitter** → External
- **Email** → mailto:

## Content Organization

### Blog Posts
Located in: `_posts/YYYY-MM-DD-slug.md`

```
_posts/
├── 2024-11-05-fullstack-platform.md
├── 2024-10-28-react-testing.md
├── 2024-10-15-mvc-architecture.md
└── 2024-10-01-docker-fundamentals.md
```

### Projects
Located in: `_projects/NN-slug.md`

```
_projects/
├── 01-peercafe.md
├── 02-maze-mvc.md
└── 03-hangman.md
```

## User Flows

### Visitor Flow 1: Discover Projects
```
Home → Featured Projects → View Details → Project Page
                          ↓
                    (Technology, Role, Link)
```

### Visitor Flow 2: Read Blog
```
Home → View All Posts → Blog Listing → Blog Post
                          ↓
                      (By Tag or Date)
```

### Visitor Flow 3: Learn About
```
Home → About Section → /about → Full Bio → Contact
```

### Visitor Flow 4: Contact
```
Home → Contact Section → Social Links → External Platforms
       /about
       /projects
       /blog
```

## Responsive Breakpoints

| Device | Width | Navigation |
|--------|-------|-----------|
| Mobile | < 480px | Hamburger menu |
| Tablet | 480px - 768px | Hamburger menu |
| Desktop | > 768px | Horizontal menu |

## Content Sections

### Homepage Sections
1. **Navbar** (fixed at top)
   - Logo/Title
   - Navigation Links
   - Mobile Toggle

2. **Hero Section**
   - Large Title
   - Subtitle
   - Description
   - CTA Buttons

3. **Projects Section**
   - Section Title
   - Project Cards Grid
   - Each Card: Title, Techs, Description, Link

4. **About Section**
   - Section Title
   - About Text

5. **Skills Section**
   - Skill Categories Grid
   - Frontend, Backend, Tools

6. **Blog Section**
   - Section Title
   - Latest Posts
   - View All Link

7. **Contact Section**
   - Description
   - Social Links
   - Email Link

8. **Footer**
   - Site Info
   - Quick Links
   - Social Links
   - Copyright

## SEO Elements

- **Title Tags**: Unique for each page
- **Meta Descriptions**: In front matter
- **Canonical URLs**: Automatic
- **Sitemap**: Auto-generated at `/sitemap.xml`
- **RSS Feed**: Auto-generated at `/feed.xml`
- **Social Sharing**: Proper meta tags

## Interactive Elements

### Navbar
- Smooth scroll to sections
- Mobile hamburger toggle
- Sticky position
- Hover effects on links

### Project Cards
- Hover: Lift up, shadow increase
- Click: Navigate to details
- Responsive: Grid adapts to screen

### Blog Cards
- Hover: Highlight effect
- Click: Open post
- Tags: Clickable filters

### Buttons
- Hover: Color change, transform
- Active: Visual feedback
- Mobile: Full width if needed

## Performance Considerations

- **Static Generation**: All content pre-built
- **CSS**: Single optimized file
- **JavaScript**: Minimal, vanilla
- **Images**: Optimized format recommendations
- **Caching**: GitHub Pages handles caching

## Future Enhancement Ideas

- [ ] Search functionality
- [ ] Dark mode toggle
- [ ] Project filtering
- [ ] Comment system on posts
- [ ] Analytics dashboard
- [ ] Newsletter signup
- [ ] Related posts
- [ ] Reading time estimates
- [ ] Social share buttons
- [ ] Tags page with cloud

---

This structure ensures excellent user experience and SEO performance while maintaining simplicity and ease of maintenance.
