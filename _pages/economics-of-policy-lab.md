---
layout: single
title: "Economics of Policy Lab"
permalink: /economics-of-policy-lab/
author_profile: true
---

{% include base_path %}
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
    {% if section.members.size == 0 %}
      <p class="lab-section__empty">Positions to be announced soon.</p>
    {% else %}
      <div class="lab-members">
        {% for member in section.members %}
          <article class="lab-member" id="{{ member.id }}">
            {% if member.image %}
              <img class="lab-member__photo" src="{{ member.image | prepend: '/' | prepend: base_path }}" alt="{{ member.name }}" />
            {% endif %}
            <h3>{{ member.name }}</h3>
            <p class="lab-member__role">{{ member.role }}</p>
            <p class="lab-member__tagline">{{ member.tagline }}</p>
            <p>{{ member.bio }}</p>
            <p><a href="mailto:{{ member.contact_email | default: member.email }}">{{ member.email }}</a></p>
            {% if member.education %}
              <h4>Education</h4>
              <ul class="lab-member__education">
                {% for education in member.education %}
                  <li>{{ education.degree }}, {{ education.institution }} ({{ education.year }})</li>
                {% endfor %}
              </ul>
            {% endif %}
          </article>
        {% endfor %}
      </div>
    {% endif %}
  </section>
{% endfor %}
