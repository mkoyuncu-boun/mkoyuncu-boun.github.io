---
layout: single
title: "Economics of Policy Lab"
permalink: /economics-of-policy-lab/
author_profile: true
---

{% assign lab = site.data.economics_of_policy_lab %}

<section class="lab-recruitment" aria-labelledby="open-positions">
  <h2 id="open-positions">{{ lab.recruitment_banner.title }}</h2>
  <p>{{ lab.recruitment_banner.description }}</p>
  <ul>
    {% for opening in lab.recruitment_banner.openings %}
      <li>{{ opening }}</li>
    {% endfor %}
  </ul>
</section>

{% for section in lab.sections %}
  <section class="lab-section" aria-labelledby="{{ section.category | slugify }}">
    <h2 id="{{ section.category | slugify }}">{{ section.category }}</h2>
    <div class="lab-members">
      {% for member in section.members %}
        <article class="lab-member" id="{{ member.id }}">
          <h3>{{ member.name }}</h3>
          <p class="lab-member__role">{{ member.role }}</p>
          <p class="lab-member__tagline">{{ member.tagline }}</p>
          <p>{{ member.bio }}</p>
          <p><a href="mailto:{{ member.email }}">{{ member.email }}</a></p>
          <h4>Education</h4>
          <ul class="lab-member__education">
            {% for education in member.education %}
              <li>{{ education.degree }}, {{ education.institution }} ({{ education.year }})</li>
            {% endfor %}
          </ul>
        </article>
      {% endfor %}
    </div>
  </section>
{% endfor %}
