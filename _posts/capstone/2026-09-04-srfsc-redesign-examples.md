---
microblog: true
toc: false
layout: post
title: SRFSC Website Redesign Examples
description: Visual mockup examples showing how the Scripps Ranch Fire Safe Council website could be redesigned for clarity, urgency, and action.
permalink: /capstone/srfsc/
author: Krish Kelageri, Jasan Boprai, Shourya Patel
year: "2026-2027"
---

<div class="comms-infograph">
  <div class="comms-header">
    <div class="comms-badge">Design-Based Research Capstone</div>
    <h1 class="comms-title">SRFSC Website Redesign Examples</h1>
    <p class="comms-description">The SRFSC homepage can be more direct and action-focused. The strongest example is to make the mission, volunteer path, and urgent neighborhood context visible immediately.</p>
  </div>

</div>

<div class="capstone-kanban-embed srfsc-kanban-board">
{% include ocs_kanban_board.html url="https://github.com/orgs/SRFSC-Organization/projects/1" title="SRFSC Project Board" %}
</div>

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
  /* Keep this board's presentation entirely within the SRFSC page. */
  .srfsc-kanban-board > [data-ocs-kanban] {
    --pref-text-color: #e6edf3;
    --text-muted: #ababab;
    --pref-accent-color: #3b82f6;
    --panel: #292929;
    --ui-border: #383838;
    min-width: 0;
    max-width: 100%;
    margin-bottom: 2rem;
    padding: 1rem;
    border: 0;
    background: #292929;
    box-shadow: none;
    color: #e6edf3;
  }

  .srfsc-kanban-board [data-hook="mount"],
  .srfsc-kanban-board .ocs__keypoints {
    min-width: 0;
    max-width: 100%;
  }

  .srfsc-kanban-board [data-ocs-kanban] > .ocs__links {
    margin-bottom: 1rem;
  }

  .srfsc-kanban-board .ocs__links {
    gap: 0.65rem;
    flex-wrap: wrap;
  }

  .srfsc-kanban-board .ocs__btn.pill {
    background: #1b2230;
    border-color: transparent;
    color: #3b82f6;
  }

  .srfsc-kanban-board .ocs__btn[aria-pressed="true"] {
    background: #142b4b;
    color: #e6edf3;
  }

  .srfsc-kanban-board .ocs__kanban-board {
    grid-auto-columns: minmax(min(16rem, 100%), 1fr);
    gap: 0.85rem;
    margin: 0;
    padding: 0 0 0.5rem;
    list-style: none;
  }

  .srfsc-kanban-board .ocs__kanban-column {
    gap: 0.75rem;
    padding: 0.85rem;
    border: 1px solid #383838;
    border-top: 3px solid #3b82f6;
    border-radius: 0.75rem;
    background: #303030;
    color: #e6edf3 !important;
  }

  .srfsc-kanban-board .ocs__kanban-column[data-stage="todo"] {
    border-top-color: #5878a2;
  }

  .srfsc-kanban-board .ocs__kanban-column > div:first-child {
    display: flex;
    align-items: center;
    gap: 0.4rem;
    margin-bottom: 0.35rem;
    font-size: 1.05rem;
    color: #e6edf3 !important;
  }

  .srfsc-kanban-board .ocs__status-pill--neutral {
    background: #2c2c2c;
    border: 1px solid #3a3a3a;
    color: #ababab !important;
    font-size: 0.75rem;
  }

  .srfsc-kanban-board .ocs__kanban-item {
    padding: 0.75rem;
    border-radius: 0.65rem;
    border: 1px solid #353535;
    background: #292929;
    overflow-wrap: anywhere;
  }

  .srfsc-kanban-board .ocs__kanban-item:hover,
  .srfsc-kanban-board .ocs__kanban-item:focus-visible {
    background: #2b3038;
    border-color: #3b82f6;
  }

  .srfsc-kanban-board .ocs__kanban-kicker {
    font-size: 0.68rem;
    letter-spacing: 0.035em;
    color: #ababab !important;
  }

  .srfsc-kanban-board .ocs__kanban-name {
    font-size: 0.95rem;
    font-weight: 700;
    line-height: 1.4;
    color: #e6edf3 !important;
  }

  .srfsc-kanban-board .ocs__kanban-note {
    font-size: 0.85rem;
    line-height: 1.4;
    color: #ababab !important;
  }

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
