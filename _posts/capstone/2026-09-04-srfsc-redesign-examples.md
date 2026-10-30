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

<div class="comms-infograph" id="srfsc-capstone">
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

<section class="ocs__card ocs__keypoints" id="srfsc-page-backlog" aria-labelledby="srfsc-backlog-title">
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

<script type="module" id="srfsc-board-details">
  import { readEntry, writeEntry, cacheState } from '{{ site.baseurl }}/assets/js/kanban-board.js';

  const section = document.querySelector('#srfsc-capstone [data-ocs-kanban]');
  const mount = section.querySelector('[data-hook="mount"]');
  const backlogSource = document.getElementById('srfsc-page-backlog');
  const names = new Map([['jas-bop', 'Jasan'], ['thecoder203', 'Krish'], ['shouryap4123', 'Shourya'], ['shouryap4132', 'Shourya']]);
  const state = { owner: 'All', backlog: false, expanded: new Set() };
  let issues = new Map();
  let ownersReady = false;

  function node(tag, className, text) {
    const result = document.createElement(tag);
    result.className = className;
    if (text !== undefined) result.textContent = text;
    return result;
  }

  const displayName = (login) => names.get(login.toLowerCase()) || login;
  const toolbar = node('div', 'ocs__links srfsc-board-controls');
  toolbar.append(node('span', 'ocs__text', 'Team'));
  ['All', 'Jasan', 'Krish', 'Shourya'].forEach((name) => {
    const button = node('button', 'ocs__btn small pill', name);
    button.type = 'button';
    button.dataset.owner = name;
    button.addEventListener('click', () => { state.owner = name; state.expanded.clear(); enhance(); });
    toolbar.append(button);
  });
  const toggle = node('label', 'ocs__toggle');
  const input = node('input', 'ocs__toggle-input');
  input.type = 'checkbox';
  input.setAttribute('aria-label', 'Show planned backlog tasks');
  const track = node('span', 'ocs__toggle-track');
  track.setAttribute('aria-hidden', 'true');
  const toggleLabel = node('span', 'ocs__toggle-label');
  toggleLabel.title = 'Planned tasks maintained on this capstone page, plus any GitHub backlog items.';
  toggle.append(input, track, toggleLabel);
  toolbar.append(toggle);
  input.addEventListener('change', () => {
    state.backlog = input.checked;
    const sharedToggle = mount.querySelector('[data-expand]');
    if (sharedToggle && sharedToggle.checked !== state.backlog) {
      sharedToggle.checked = state.backlog;
      sharedToggle.dispatchEvent(new Event('change'));
    }
    enhance();
  });

  function localBacklog() {
    const column = node('li', 'ocs__kanban-column');
    column.dataset.stage = 'backlog';
    column.dataset.localBacklog = '';
    const heading = node('div', 'srfsc-column-heading');
    const tasks = [...backlogSource.querySelectorAll('li')];
    heading.append(node('strong', '', 'Backlog'), node('span', 'ocs__status-pill ocs__status-pill--neutral', String(tasks.length)));
    column.append(heading);
    tasks.forEach((task) => {
      const card = node('div', 'ocs__kanban-item');
      card.append(node('div', 'ocs__kanban-kicker', 'SRFSC · Planned follow-up'));
      card.append(node('div', 'ocs__kanban-name', task.querySelector('strong').textContent.replace(/:$/, '')));
      const description = task.cloneNode(true);
      description.querySelector('strong').remove();
      card.append(node('div', 'ocs__kanban-note', description.textContent.trim()));
      const links = node('div', 'ocs__links');
      task.querySelectorAll('a').forEach((source) => links.append(source.cloneNode(true)));
      card.append(links);
      column.append(card);
    });
    column.hidden = !state.backlog;
    return column;
  }

  function decorateCard(card) {
    const issue = issues.get(card.href);
    if (!issue) return [];
    // Replace raw GitHub logins while retaining shipped dates and field notes.
    card.querySelectorAll('.ocs__kanban-note:not(.srfsc-owner)').forEach((note) => {
      const parts = note.textContent.split(' · ');
      if (issue.logins.some((login) => parts[0].toLowerCase().includes(login.toLowerCase()))) {
        if (parts.length > 1) note.textContent = parts.slice(1).join(' · ');
        else note.remove();
      }
    });
    let owner = card.querySelector('.srfsc-owner');
    if (!owner) {
      owner = node('div', 'ocs__kanban-note srfsc-owner');
      card.querySelector('.ocs__kanban-name').after(owner);
    }
    const date = [...card.querySelectorAll('.ocs__kanban-note:not(.srfsc-owner)')].find((note) => /^(Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Oct|Nov|Dec) \d{1,2}$/.test(note.textContent));
    if (date) { card.dataset.shipped = date.textContent; date.remove(); }
    const people = issue.people.join(', ') || 'Unassigned';
    owner.textContent = [people, card.dataset.shipped].filter(Boolean).join(' · ');
    owner.title = `${issue.kind}: ${people}`;
    let kicker = card.querySelector('.ocs__kanban-kicker');
    if (!kicker) { kicker = node('div', 'ocs__kanban-kicker'); card.prepend(kicker); }
    kicker.textContent = 'SRFSC';
    if (card.closest('[data-stage]').dataset.stage !== 'done' && ![...card.querySelectorAll('.ocs__kanban-note')].some((note) => /^Priority:/i.test(note.textContent))) {
      owner.after(node('div', 'ocs__kanban-note', `Priority: ${issue.priority || 'Not set'}`));
    }
    return issue.people;
  }

  function decorateColumn(column) {
    const key = column.dataset.stage || column.firstElementChild.textContent;
    const cards = [...column.querySelectorAll('a.ocs__kanban-item')];
    const matching = cards.filter((card) => {
      const people = decorateCard(card);
      return state.owner === 'All' || people.includes(state.owner);
    });
    const visible = new Set(state.expanded.has(key) ? matching : matching.slice(0, 5));
    cards.forEach((card) => { card.hidden = !visible.has(card); });
    column.firstElementChild.querySelector('.ocs__status-pill').textContent = String(matching.length);
    column.querySelector('[data-column-toggle]')?.parentElement.remove();
    column.querySelector('[data-srfsc-more]')?.remove();
    if (matching.length > 5) {
      const more = node('button', 'ocs__status-pill ocs__status-pill--neutral srfsc-more', state.expanded.has(key) ? 'Show less' : `+${matching.length - 5} more`);
      more.type = 'button';
      more.dataset.srfscMore = key;
      more.setAttribute('aria-expanded', String(state.expanded.has(key)));
      more.addEventListener('click', () => {
        if (state.expanded.has(key)) state.expanded.delete(key);
        else state.expanded.add(key);
        enhance();
        [...mount.querySelectorAll('[data-srfsc-more]')].find((button) => button.dataset.srfscMore === key)?.focus();
      });
      column.append(more);
    }
  }

  const observer = new MutationObserver(enhance);
  function enhance() {
    observer.disconnect();
    try {
      // Load the shared renderer's remaining cards before applying local filters.
      let more;
      while ((more = mount.querySelector('[data-column-toggle][aria-expanded="false"]'))) more.click();
      const columns = mount.querySelector('.ocs__kanban-board');
      if (!columns) return;
      columns.parentElement.prepend(toolbar);
      toolbar.querySelectorAll('[data-owner]').forEach((button) => {
        const selected = button.dataset.owner === state.owner;
        button.className = `ocs__btn small pill${selected ? ' accent fill' : ''}`;
        button.setAttribute('aria-pressed', String(selected));
        button.disabled = button.dataset.owner !== 'All' && !ownersReady;
      });
      const sharedToggle = mount.querySelector('[data-expand]');
      if (sharedToggle) sharedToggle.closest('label').hidden = true;
      const liveBacklog = Number(sharedToggle?.closest('label').textContent.match(/\((\d+)\)/)?.[1] || 0);
      toggleLabel.textContent = `💡 Backlog (${backlogSource.querySelectorAll('li').length + liveBacklog})`;
      if (!columns.querySelector('[data-stage="review"]')) {
        const review = node('li', 'ocs__kanban-column');
        review.dataset.stage = 'review';
        const heading = node('div', 'srfsc-column-heading');
        heading.append(node('strong', '', 'In review'), node('span', 'ocs__status-pill ocs__status-pill--neutral', '0'));
        review.append(heading, node('div', 'ocs__text', 'Nothing here'));
        columns.insertBefore(review, columns.querySelector('[data-stage="done"]'));
      }
      columns.querySelector('[data-local-backlog]')?.remove();
      [...columns.children].forEach(decorateColumn);
      columns.prepend(localBacklog());
      backlogSource.hidden = true;
    } finally {
      observer.observe(mount, { childList: true, subtree: true });
    }
  }
  enhance();

  async function loadOwners() {
    const cacheKey = 'srfsc:issue-owners:v1';
    const cached = readEntry(cacheKey);
    if (cached?.board) {
      issues = new Map(cached.board);
      ownersReady = true;
      enhance();
      if (cacheState(cached, Date.now()) === 'fresh') return;
    }
    try {
      const loaded = [];
      let url = 'https://api.github.com/orgs/SRFSC-Organization/projectsV2/1/items?per_page=100';
      for (let page = 0; url && page < 5; page += 1) {
        const response = await fetch(url, { headers: { Accept: 'application/vnd.github+json', 'X-GitHub-Api-Version': '2022-11-28' } });
        if (!response.ok) throw new Error(`GitHub returned ${response.status}`);
        const items = await response.json();
        items.forEach(({ content }) => {
          if (!content?.html_url) return;
          const assigned = (content.assignees || []).map((person) => person.login);
          const logins = assigned.length ? assigned : [content.user?.login].filter(Boolean);
          const priority = (content.labels || []).map((label) => /^(?:priority\s*:\s*)?(high|medium|low|urgent)$/i.exec(typeof label === 'string' ? label : label.name || '')).find(Boolean);
          loaded.push([content.html_url, { logins, people: [...new Set(logins.map(displayName))], kind: assigned.length ? 'Assigned to' : 'Created by', priority: priority?.[1] || '' }]);
        });
        url = /<([^>]+)>;\s*rel="next"/.exec(response.headers.get('link') || '')?.[1] || '';
        if (url && !url.startsWith('https://api.github.com/orgs/SRFSC-Organization/projectsV2/1/items?')) throw new Error('Unexpected GitHub pagination URL');
      }
      issues = new Map(loaded);
      ownersReady = true;
      writeEntry(cacheKey, { fetchedAt: Date.now(), board: loaded });
      enhance();
    } catch (error) {
      const status = node('p', 'ocs__text', `Unable to refresh issue owners. ${error.message}`);
      status.setAttribute('role', 'status');
      section.append(status);
    }
  }
  loadOwners();
</script>

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
  #srfsc-capstone [data-ocs-kanban] [hidden],
  #srfsc-page-backlog[hidden] { display: none !important; }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-board {
    grid-auto-columns: minmax(min(15rem, 100%), 1fr);
    gap: 1rem;
  }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-column {
    gap: 1rem;
    padding: 1rem;
  }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-item {
    padding: 0.85rem;
  }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-name {
    font-size: clamp(1rem, 1vw, 1.25rem);
    font-weight: 700;
  }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-kicker {
    font-size: clamp(0.75rem, 0.7vw, 0.875rem);
  }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-note {
    font-size: clamp(0.875rem, 0.9vw, 1.125rem);
  }
  #srfsc-capstone [data-ocs-kanban] > .ocs__links,
  #srfsc-capstone [data-ocs-kanban] .srfsc-board-controls .ocs__btn,
  #srfsc-capstone [data-ocs-kanban] .srfsc-board-controls .ocs__text,
  #srfsc-capstone [data-ocs-kanban] .ocs__toggle-label {
    font-size: clamp(1rem, 1vw, 1.25rem);
  }
  #srfsc-capstone [data-ocs-kanban] .srfsc-column-heading,
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-column > div:first-child {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 0.25rem;
    font-size: clamp(1.15rem, 1.15vw, 1.5rem);
  }
  #srfsc-capstone [data-ocs-kanban] .ocs__kanban-note {
    color: var(--text-muted) !important;
  }
  #srfsc-capstone [data-ocs-kanban] .srfsc-more {
    justify-self: start;
    cursor: pointer;
    font: inherit;
    font-size: 0.8rem;
  }
  #srfsc-capstone [data-ocs-kanban] .srfsc-board-controls { flex-wrap: wrap; }
  @media (min-width: 1200px) {
    #srfsc-capstone > [data-ocs-kanban] {
      position: relative;
      left: 50%;
      width: calc(100vw - 64px);
      max-width: none;
      transform: translateX(-50%);
    }
  }
  @media (max-width: 600px) {
    #srfsc-capstone [data-ocs-kanban] .ocs__kanban-board { grid-auto-columns: 88%; }
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
