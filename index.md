---
layout: default
---

<div class="hero">
  <h1 class="hero-title">Hi, I'm Mason</h1>
  <p class="hero-subtitle">Software Engineer & Full-Stack Developer</p>
  <p class="hero-description">
    I build scalable web applications, mobile solutions, and developer tools. 
    Passionate about clean code, open source, and solving complex problems.
  </p>
  <div class="hero-buttons">
    <a href="#projects" class="btn btn-primary">View My Projects</a>
    <a href="#about" class="btn btn-secondary">Learn More</a>
  </div>
</div>

<section id="projects" class="projects-section">
  <h2>Featured Projects</h2>
  <div class="projects-grid">
    {% for project in site.projects %}
    <div class="project-card">
      <div class="project-header">
        <h3><a href="{{ project.url }}">{{ project.title }}</a></h3>
        {% if project.tags %}
        <div class="project-tags">
          {% for tag in project.tags %}
          <span class="tag">{{ tag }}</span>
          {% endfor %}
        </div>
        {% endif %}
      </div>
      <p class="project-description">{{ project.description }}</p>
      {% if project.link %}
      <a href="{{ project.link }}" class="project-link" target="_blank">View Project →</a>
      {% endif %}
    </div>
    {% endfor %}
  </div>
</section>

<section id="about" class="about-section">
  <h2>About Me</h2>
  <div class="about-content">
    <p>
      I'm a passionate software engineer with experience in full-stack web development, 
      Java, Python, and modern JavaScript frameworks. I enjoy building intuitive user interfaces 
      and robust backend systems.
    </p>
    <p>
      My interests include open-source development, cloud technologies, and creating 
      solutions that make a positive impact.
    </p>
  </div>
</section>

<section id="skills" class="skills-section">
  <h2>Skills & Technologies</h2>
  <div class="skills-grid">
    <div class="skill-category">
      <h3>Frontend</h3>
      <ul>
        <li>React / Next.js</li>
        <li>TypeScript</li>
        <li>HTML / CSS / Tailwind</li>
        <li>Material-UI</li>
      </ul>
    </div>
    <div class="skill-category">
      <h3>Backend</h3>
      <ul>
        <li>Node.js / Express</li>
        <li>Python / FastAPI</li>
        <li>Java / Spring Boot</li>
        <li>PostgreSQL / MongoDB</li>
      </ul>
    </div>
    <div class="skill-category">
      <h3>Tools & DevOps</h3>
      <ul>
        <li>Git / GitHub</li>
        <li>Docker</li>
        <li>CI/CD Pipelines</li>
        <li>AWS / Azure</li>
      </ul>
    </div>
  </div>
</section>

<section id="blog" class="blog-section">
  <h2>Latest Posts</h2>
  <div class="posts-list">
    {% for post in site.posts limit:3 %}
    <article class="post-preview">
      <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
      <p class="post-date">{{ post.date | date: "%B %d, %Y" }}</p>
      <p class="post-excerpt">{{ post.excerpt }}</p>
      <a href="{{ post.url }}" class="read-more">Read More →</a>
    </article>
    {% endfor %}
  </div>
  {% if site.posts.size > 3 %}
  <a href="/blog" class="view-all">View All Posts</a>
  {% endif %}
</section>

<section id="contact" class="contact-section">
  <h2>Get In Touch</h2>
  <p>
    I'm always interested in hearing about new projects and opportunities. 
    Feel free to reach out!
  </p>
  <div class="contact-links">
    {% if site.author.github %}
    <a href="https://github.com/{{ site.author.github }}" class="contact-link" target="_blank">
      GitHub
    </a>
    {% endif %}
    {% if site.author.linkedin %}
    <a href="https://linkedin.com/in/{{ site.author.linkedin }}" class="contact-link" target="_blank">
      LinkedIn
    </a>
    {% endif %}
    {% if site.author.twitter %}
    <a href="https://twitter.com/{{ site.author.twitter }}" class="contact-link" target="_blank">
      Twitter
    </a>
    {% endif %}
    {% if site.author.email %}
    <a href="mailto:{{ site.author.email }}" class="contact-link">
      Email
    </a>
    {% endif %}
  </div>
</section>
