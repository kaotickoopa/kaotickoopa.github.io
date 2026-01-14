---
layout: page
title: Blog
permalink: /blog/
---

# Blog Posts

Explore my thoughts on software development, best practices, and lessons learned from building real-world applications.

<div class="blog-container">
  {% if site.posts.size == 0 %}
    <p class="no-posts">No posts yet. Check back soon!</p>
  {% else %}
    <div class="posts-grid">
      {% for post in site.posts %}
      <article class="blog-card">
        <header class="blog-card-header">
          <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
          <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%B %d, %Y" }}
          </time>
        </header>
        
        {% if post.excerpt %}
        <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
        {% endif %}
        
        {% if post.tags %}
        <footer class="blog-card-footer">
          <div class="post-tags-inline">
            {% for tag in post.tags %}
            <a href="/blog/tags/{{ tag | slugify }}" class="tag-link">{{ tag }}</a>
            {% endfor %}
          </div>
        </footer>
        {% endif %}
        
        <a href="{{ post.url }}" class="read-more-link">Read Full Post →</a>
      </article>
      {% endfor %}
    </div>
  {% endif %}
</div>

<style>
  .blog-container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .posts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
  }

  .blog-card {
    background: white;
    border-radius: 8px;
    padding: 1.5rem;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    display: flex;
    flex-direction: column;
  }

  .blog-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  }

  .blog-card-header h2 {
    margin: 0 0 0.5rem 0;
    font-size: 1.3em;
  }

  .blog-card-header h2 a {
    color: #2c3e50;
  }

  .blog-card-header h2 a:hover {
    color: #3498db;
  }

  .post-date {
    color: #999;
    font-size: 0.9em;
  }

  .post-excerpt {
    color: #666;
    margin: 1rem 0;
    flex-grow: 1;
    line-height: 1.6;
  }

  .blog-card-footer {
    margin: 1rem 0;
  }

  .post-tags-inline {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .tag-link {
    background: #f0f0f0;
    color: #3498db;
    padding: 0.25em 0.75em;
    border-radius: 20px;
    font-size: 0.85em;
    transition: background 0.3s ease;
  }

  .tag-link:hover {
    background: #3498db;
    color: white;
  }

  .read-more-link {
    color: #3498db;
    font-weight: 600;
    display: inline-block;
    margin-top: auto;
  }

  .read-more-link:hover {
    color: #e74c3c;
  }

  .no-posts {
    text-align: center;
    color: #999;
    padding: 3rem;
    font-style: italic;
  }

  @media (max-width: 768px) {
    .posts-grid {
      grid-template-columns: 1fr;
    }
  }
</style>
