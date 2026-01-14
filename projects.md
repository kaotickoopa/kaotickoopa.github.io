---
layout: page
title: Projects
permalink: /projects/
---

# My Projects

A collection of projects showcasing my skills in full-stack development, software architecture, and problem-solving.

<div class="projects-container">
  {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
  
  {% if sorted_projects.size == 0 %}
    <p class="no-projects">No projects yet. Check back soon!</p>
  {% else %}
    <div class="projects-detailed">
      {% for project in sorted_projects %}
      <article class="project-item">
        <div class="project-content">
          <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
          <p class="project-subtitle">{{ project.subtitle }}</p>
          
          {% if project.description %}
          <p class="project-description">{{ project.description }}</p>
          {% endif %}
          
          {% if project.technologies %}
          <div class="technologies">
            <strong>Tech Stack:</strong>
            <div class="tech-list">
              {% for tech in project.technologies %}
              <span class="tech-badge">{{ tech }}</span>
              {% endfor %}
            </div>
          </div>
          {% endif %}
          
          {% if project.role %}
          <p class="project-role"><strong>Role:</strong> {{ project.role }}</p>
          {% endif %}
          
          <footer class="project-footer">
            <a href="{{ project.url }}" class="project-detail-link">View Details →</a>
            {% if project.link %}
            <a href="{{ project.link }}" class="project-external-link" target="_blank" rel="noopener">
              View Repository ↗
            </a>
            {% endif %}
          </footer>
        </div>
      </article>
      {% endfor %}
    </div>
  {% endif %}
</div>

<style>
  .projects-container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .projects-detailed {
    display: grid;
    gap: 2rem;
    margin-top: 2rem;
  }

  .project-item {
    background: white;
    border-left: 4px solid #3498db;
    border-radius: 8px;
    padding: 2rem;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
  }

  .project-item:hover {
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
    transform: translateX(5px);
  }

  .project-content h2 {
    margin: 0 0 0.5rem 0;
    font-size: 1.6em;
  }

  .project-content h2 a {
    color: #2c3e50;
  }

  .project-content h2 a:hover {
    color: #3498db;
  }

  .project-subtitle {
    color: #666;
    font-style: italic;
    margin: 0 0 1rem 0;
  }

  .project-description {
    color: #555;
    line-height: 1.6;
    margin: 1rem 0;
  }

  .technologies {
    margin: 1.5rem 0;
  }

  .technologies strong {
    color: #2c3e50;
    display: block;
    margin-bottom: 0.5rem;
  }

  .tech-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .tech-badge {
    background: linear-gradient(135deg, #3498db, #2980b9);
    color: white;
    padding: 0.35em 0.75em;
    border-radius: 20px;
    font-size: 0.9em;
    font-weight: 500;
  }

  .project-role {
    color: #666;
    margin: 1rem 0;
  }

  .project-footer {
    display: flex;
    gap: 1rem;
    margin-top: 1.5rem;
    flex-wrap: wrap;
  }

  .project-detail-link,
  .project-external-link {
    padding: 0.5rem 1rem;
    border-radius: 5px;
    font-weight: 600;
    transition: all 0.3s ease;
    display: inline-block;
  }

  .project-detail-link {
    background: #3498db;
    color: white;
  }

  .project-detail-link:hover {
    background: #2980b9;
    transform: translateY(-2px);
  }

  .project-external-link {
    border: 2px solid #3498db;
    color: #3498db;
  }

  .project-external-link:hover {
    background: #3498db;
    color: white;
  }

  .no-projects {
    text-align: center;
    color: #999;
    padding: 3rem;
    font-style: italic;
  }

  @media (max-width: 768px) {
    .project-item {
      padding: 1.5rem;
    }

    .project-content h2 {
      font-size: 1.3em;
    }

    .project-footer {
      flex-direction: column;
    }

    .project-footer a {
      width: 100%;
      text-align: center;
    }
  }
</style>
