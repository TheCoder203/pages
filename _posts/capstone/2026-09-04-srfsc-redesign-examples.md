---
microblog: true
toc: false
layout: post
title: SRFSC Website Redesign Examples
description: Visual mockup examples showing how the Scripps Ranch Fire Safe Council website could be redesigned for clarity, urgency, and action.
permalink: /capstone/srfsc/
author: Krish Kelageri, Jasan Boprai, Shourya Patel
year: "2026-2027"
Board:
  url: "https://github.com/orgs/SRFSC-Organization/projects/1"
  filter: "Team"
  columns:
    - status: "Team Map"
      hidden: true
    - status: "Reflections"
      hidden: true
---

<section class="ocs__card ocs__keypoints" id="about-srfsc" aria-labelledby="about-srfsc-title">
  <h2 id="about-srfsc-title">About Scripps Ranch Fire Safe Council</h2>
  <p>Founded in 2004, SRFSC is a volunteer-led 501(c)(3) serving 12,000 Scripps Ranch homes through wildfire education, vegetation management, and partnerships.</p>

  <h3>History and milestones</h3>
  <ul>
    <li><strong>2003:</strong> Cedar Fire destroyed 312 homes. Flames stopped 70 feet from Chimney Canyon, threatening 200 more. Residents formed Chimney Canyon council to address dead eucalyptus and accumulated fuel.</li>
    <li><strong>2004:</strong> San Diego County’s first urban Fire Safe Council incorporated. Two federal grants and Conservation Corps support enabled a 100-foot firebreak.</li>
    <li><strong>2005:</strong> Partnership with the Civic Association brought the SRFSC name, community-wide coverage, and a 12-agency alliance.</li>
    <li><strong>2007:</strong> Preparedness helped protect homes during the Witch Creek Fire.</li>
  </ul>

  <h3>Work and impact</h3>
  <p>Impact: 650+ firebreaks, 340 hazardous trees removed, 165 trees planted, and six trails cleared.</p>
  <p>Programs include defensible-space work with homeowners and the City, monthly newsletters, open houses, and the annual Play to Protect Golf Tournament. Partners include CAL FIRE, San Diego Fire-Rescue, the Civic Association, and California Conservation Corps.</p>

  <h3>Leadership</h3>
  <p>President: Kristin Rayder. Treasurer: Jessie Gates. Secretary: Karen Herreros. Directors: Dave Mason, Sandy Wetzel-Smith, Chad Smith.</p>

  <h3>Contact and involvement</h3>
  <p><a href="tel:+18582013711">858-201-3711</a> · <a href="mailto:srfiresafecouncil@gmail.com">srfiresafecouncil@gmail.com</a><br>9903 Businesspark Ave #102, San Diego, CA 92131.</p>
  <p>Volunteers and donations support ongoing prevention.</p>
  <p class="ocs__text">Summarized from <a href="https://srfiresafe.org/about/" target="_blank" rel="noopener noreferrer">SRFSC’s organization overview</a>.</p>
</section>

{% assign data = page %}

<div class="comms-infograph">
  <div class="comms-header">
    <div class="comms-badge">Design-Based Research Capstone</div>
    <h1 class="comms-title">SRFSC Website Redesign Examples</h1>
    <p class="comms-description">The SRFSC homepage can be more direct and action-focused. The strongest example is to make the mission, volunteer path, and urgent neighborhood context visible immediately.</p>
  </div>

  <!-- Sprint Board: live from the team's GitHub project -->
  {% if data.Board %}
  {% include ocs_kanban_board.html url=data.Board.url filter=data.Board.filter columns=data.Board.columns %}
  {% endif %}
</div>

<section class="ocs__card ocs__keypoints" aria-labelledby="srfsc-backlog-title">
  <h2 id="srfsc-backlog-title">SRFSC backlog</h2>
  <p>Planned follow-up work based on our open project issues.</p>
  <ul>
    <li><strong>Verify deployed member login and profiles:</strong> connect the hosted frontend to the SRFSC account backend and check sign-in, saved profile data, and logout. Sources: <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/6">#6</a>, <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/8">#8</a>.</li>
    <li><strong>Test hazard reporting end to end:</strong> check required fields, invalid input, successful submission, confirmation messages, and council review. Source: <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/10">#10</a>.</li>
    <li><strong>Explore an active-fire map:</strong> evaluate how to present current incidents with links to official CAL FIRE information. Source: <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/12">#12</a>.</li>
    <li><strong>Add an interactive readiness check:</strong> help residents review their preparedness and find relevant next steps. Source: <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/2">#2</a>.</li>
    <li><strong>Refine the homepage hub:</strong> reduce scrolling and make volunteering, hazard reporting, and preparedness resources easier to find. Sources: <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/2">#2</a>, <a href="https://github.com/SRFSC-Organization/capstone2pages/issues/4">#4</a>.</li>
  </ul>
</section>

<!-- markdownlint-disable MD033 MD010 MD012 -->
<div class="ocs__grid ocs__grid--standard cols-2" style="margin-bottom: 1.5rem;">
    <div class="ocs__grid-cell ocs__grid-cell--header">Strengths vs Improvement</div>
    <div class="ocs__grid-cell ocs__grid-cell--accent">
        <strong>Clear Mission Messaging</strong>
        <p>Visitors should understand the wildfire risk and the council’s role before exploring the rest of the page.</p>
        <a class="ocs__btn alert-green fill small" href="{{ site.baseurl }}/capstone/srfsc/#mission">
            View Example
        </a>
    </div>
    <div class="ocs__grid-cell">
        <strong>Volunteer Path</strong>
        <p>Action buttons are easy to find and connect users directly to volunteering and donations.</p>
        <a class="ocs__btn alert-yellow fill small" href="{{ site.baseurl }}/capstone/srfsc/#actions">
            Join Us
        </a>
    </div>
    <div class="ocs__grid-cell ocs__grid-cell--accent">
        <strong>Community Trust</strong>
        <p>Local context, impact stories, and partner credibility make the council feel more established and reliable.</p>
        <a class="ocs__btn alert-green fill small" href="{{ site.baseurl }}/capstone/srfsc/#updates">
            Updates
        </a>
    </div>
    <div class="ocs__grid-cell">
        <strong>Program Clarity</strong>
        <p>Grouping fuel reduction, home hardening, and education into clear sections reduces friction and confusion.</p>
        <a class="ocs__btn alert-yellow fill small" href="{{ site.baseurl }}/capstone/srfsc/#programs">
            Program View
        </a>
    </div>
</div>

<div class="ocs__grid ocs__grid--standard cols-3" style="margin-bottom: 1.5rem;">
    <div class="ocs__grid-cell ocs__grid-cell--header">Key Opportunities</div>
    <div class="ocs__grid-cell ocs__grid-cell--accent">
        <strong>Priority First</strong>
        <p>Lead with wildfire preparedness, hazard reduction, and neighborhood action.</p>
    </div>
    <div class="ocs__grid-cell">
        <strong>Shared Visibility</strong>
        <p>Keep local news, volunteering, and donations in a single clear path.</p>
    </div>
    <div class="ocs__grid-cell ocs__grid-cell--accent">
        <strong>Clearer Identity</strong>
        <p>Use a stronger brand palette and cleaner structure to feel current and trustworthy.</p>
    </div>
</div>

<div class="ocs__grid ocs__grid--standard cols-3" style="margin-bottom: 1.5rem;">
    <div class="ocs__grid-cell ocs__grid-cell--header">What the page should emphasize</div>
    <div class="ocs__grid-cell ocs__grid-cell--accent">
        <strong>Urgency</strong>
        <p>Use a direct wildfire-risk message early so visitors understand why this matters immediately.</p>
    </div>
    <div class="ocs__grid-cell">
        <strong>Action</strong>
        <p>Volunteer, donate, and join events should be visible in one glance instead of buried in navigation.</p>
    </div>
    <div class="ocs__grid-cell ocs__grid-cell--accent">
        <strong>Trust</strong>
        <p>Neighborhood impact, local partnerships, and clear communication make the council feel credible and active.</p>
    </div>
</div>

<div style="margin-top: 1rem; margin-bottom: 1.5rem;">
    <a class="ocs__btn alert-red fill small" href="https://www.srfsc.org/" target="_blank" rel="noopener noreferrer">
        Visit the original page
    </a>
</div>

> A stronger homepage should feel calm, urgent, and clear at the same time: the message is important, the next step is obvious, and the local community feels included.

<style>
  .srfsc-mermaid-wrap {
    width: 100%;
    overflow-x: auto;
    margin: 1.5rem 0;
    padding: 0.5rem 0;
    border-radius: 12px;
    border: 1px solid rgba(23, 59, 47, 0.08);
  }

  .srfsc-mermaid-wrap .mermaid {
    min-width: 0;
    display: flex;
    justify-content: center;
  }

  .srfsc-mermaid-wrap .mermaid svg {
    max-width: 100%;
    height: auto;
    display: block;
  }
</style>

<div class="srfsc-mermaid-wrap">
  <div class="mermaid">
    flowchart TD
        A[Visitor lands on page] --> B{Understand the risk?}
        B -->|Yes| C[Read mission + local context]
        B -->|No| D[Improve hero message]
        C --> E[See call-to-action buttons]
        D --> E
        E --> F[Volunteer or donate]
        E --> G[Learn more about programs]
        F --> H[Community action grows]
        G --> H

        style A fill:#173b2f,color:#ffffff,stroke:#173b2f
        style C fill:#2f6d4c,color:#ffffff,stroke:#2f6d4c
        style E fill:#d8572a,color:#ffffff,stroke:#d8572a
        style H fill:#49615b,color:#ffffff,stroke:#49615b
  </div>
</div>
<!-- markdownlint-enable MD033 MD010 MD012 -->

## Powered by OCS grids and buttons

[Buttons]({{ '/navigation/sass/buttons/' | relative_url }}) | [Grids]({{ '/navigation/sass/grids/' | relative_url }})
