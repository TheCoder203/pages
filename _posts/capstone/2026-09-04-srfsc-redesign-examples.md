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

<div class="comms-infograph">
  <div class="comms-header">
    <div class="comms-badge">Design-Based Research Capstone</div>
    <h1 class="comms-title">SRFSC Website Redesign Examples</h1>
    <p class="comms-description">The SRFSC homepage can be more direct and action-focused. The strongest example is to make the mission, volunteer path, and urgent neighborhood context visible immediately.</p>
  </div>

</div>

<section class="srfsc-kanban-board" id="srfsc-board" aria-label="SRFSC project board">
  <div class="srfsc-board-toolbar">
    <div class="srfsc-team-filters" role="group" aria-label="Filter issues by team member"></div>
    <label class="srfsc-backlog-toggle">
      <input type="checkbox" aria-label="Show backlog">
      <span class="srfsc-toggle-track" aria-hidden="true"></span>
      <span class="srfsc-backlog-label">💡 Backlog (0)</span>
    </label>
  </div>
  <p class="srfsc-board-status" role="status">Loading the SRFSC board…</p>
  <ul class="ocs__kanban-board" aria-label="Issue columns"></ul>
  <div class="srfsc-board-footer">
    <span class="srfsc-board-meta"></span>
    <a href="https://github.com/orgs/SRFSC-Organization/projects/1" target="_blank" rel="noopener noreferrer">Open on GitHub ↗</a>
  </div>
</section>
<script type="application/json" id="srfsc-kanban-defaults">{{ site.data.kanban | jsonify | replace: "<", "\u003c" }}</script>

<script type="module" id="srfsc-owner-names">
  import { boardConfig, parseBoardUrl, refreshBoard, columnCards, readEntry, writeEntry, cacheState } from '{{ site.baseurl }}/assets/js/kanban-board.js';

  const root = document.getElementById('srfsc-board');
  const config = boardConfig(JSON.parse(document.getElementById('srfsc-kanban-defaults').textContent));
  const ownerNames = new Map([
    ['jas-bop', 'Jasan'],
    ['thecoder203', 'Krish'],
    ['shouryap4123', 'Shourya'],
    ['shouryap4132', 'Shourya'],
  ]);
  const columnLabels = [['todo', 'To do'], ['doing', 'In progress'], ['review', 'In review'], ['done', 'Done']];
  const state = { owner: 'all', backlog: false, expanded: new Set() };
  const cacheKey = 'srfsc-board:owners:v1';
  let board;

  function element(tag, className, text) {
    const node = document.createElement(tag);
    node.className = className;
    if (text !== undefined) node.textContent = text;
    return node;
  }

  function ownerName(login) {
    return ownerNames.get(login.toLowerCase()) || login;
  }

  function cardElement(card) {
    const link = element('a', 'ocs__kanban-item');
    link.href = card.url;
    link.target = '_blank';
    link.rel = 'noopener noreferrer';
    link.append(element('div', 'ocs__kanban-kicker', 'SRFSC'), element('div', 'ocs__kanban-name', card.title));
    const names = card.people.map(ownerName).join(', ') || 'Unassigned';
    const date = card.shipped ? new Date(`${card.shipped}T12:00:00`).toLocaleDateString('en-US', { month: 'short', day: 'numeric' }) : '';
    const people = element('div', 'ocs__kanban-note', [names, date].filter(Boolean).join(' · '));
    people.title = `${card.ownerKind || 'Assigned to'}: ${names}`;
    link.append(people);
    card.details.forEach(({ name, value }) => link.append(element('div', 'ocs__kanban-note', `${name}: ${value}`)));
    const proof = element('div', 'ocs__kanban-evidence');
    if (card.checklist) proof.append(element('span', 'ocs__status-pill', `☑ ${card.checklist.done}/${card.checklist.total}`));
    card.prs.forEach((pr) => proof.append(element('span', 'ocs__status-pill', `PR #${pr.number}${pr.state === 'merged' ? ' ✓' : ''}`)));
    if (proof.childElementCount) link.append(proof);
    return link;
  }

  function renderColumn(column, cards) {
    const list = columnCards(cards, column);
    const item = element('li', 'ocs__kanban-column');
    item.dataset.stage = column.stage || 'backlog';
    const heading = element('div', 'srfsc-column-heading');
    heading.append(element('strong', '', column.label), element('span', 'ocs__status-pill', String(list.length)));
    item.append(heading);
    const expanded = state.expanded.has(column.key);
    (expanded ? list : list.slice(0, 5)).forEach((card) => item.append(cardElement(card)));
    if (!list.length) item.append(element('div', 'srfsc-empty-column', 'No issues'));
    if (list.length > 5) {
      const more = element('button', 'srfsc-more', expanded ? 'Show less' : `+${list.length - 5} more`);
      more.type = 'button';
      more.dataset.column = column.key;
      more.setAttribute('aria-expanded', String(expanded));
      more.addEventListener('click', () => {
        if (expanded) state.expanded.delete(column.key);
        else state.expanded.add(column.key);
        render();
        [...root.querySelectorAll('[data-column]')].find((button) => button.dataset.column === column.key)?.focus();
      });
      item.append(more);
    }
    return item;
  }

  function render() {
    const cards = board.cards.filter((card) => state.owner === 'all' || card.people.some((name) => ownerName(name) === ownerName(state.owner)));
    const columns = columnLabels.map(([stage, label]) => board.columns.find((col) => col.stage === stage) || { key: stage, stage, label });
    // Keep custom GitHub statuses accessible alongside the four reference columns.
    const extra = board.columns.filter((col) => !columnLabels.some(([stage]) => stage === col.stage));
    const backlog = extra.filter((col) => col.collapsed || col.stage === 'backlog');
    const regular = extra.filter((col) => !backlog.includes(col));
    const count = cards.filter((card) => backlog.some((col) => col.key === card.column)).length;
    root.querySelector('.srfsc-backlog-label').textContent = `💡 Backlog (${count})`;
    const shown = [...(state.backlog ? backlog : []), ...columns, ...regular];
    root.querySelector('.ocs__kanban-board').replaceChildren(...shown.map((column) => renderColumn(column, cards)));
    root.querySelectorAll('[data-owner]').forEach((button) => button.setAttribute('aria-pressed', String(button.dataset.owner === state.owner)));
    root.querySelector('.srfsc-board-meta').textContent = `${board.cards.length} issues · Assignees shown; creator shown when unassigned`;
  }

  [['all', 'All'], ['jas-bop', 'Jasan'], ['thecoder203', 'Krish'], ['shouryap4123', 'Shourya']].forEach(([login, name]) => {
    const button = element('button', 'srfsc-team-button', name);
    button.type = 'button';
    button.dataset.owner = login;
    button.setAttribute('aria-pressed', String(login === state.owner));
    button.addEventListener('click', () => {
      state.owner = login;
      state.expanded.clear();
      if (board) render();
    });
    root.querySelector('.srfsc-team-filters').append(button);
  });
  root.querySelector('.srfsc-team-filters').prepend(element('span', 'srfsc-team-label', 'Team'));
  root.querySelector('input[type="checkbox"]').addEventListener('change', (event) => {
    state.backlog = event.target.checked;
    if (board) render();
  });

  async function loadBoard() {
    const status = root.querySelector('.srfsc-board-status');
    const saved = readEntry(cacheKey);
    if (saved?.board) {
      board = saved.board;
      render();
      status.hidden = true;
      if (cacheState(saved, Date.now()) === 'fresh') return;
    }
    const authors = new Map();
    // Project issues often have no assignee. Preserve their actual creator,
    // which the shared normalized board otherwise leaves out.
    async function fetchWithAuthors(url, options) {
      const response = await fetch(url, options);
      if (response.ok && url.includes('/items?')) {
        const items = await response.clone().json();
        items.forEach(({ content }) => {
          if (content?.user?.login) authors.set(content.html_url, content.user.login);
        });
      }
      return response;
    }
    try {
      const entry = await refreshBoard(parseBoardUrl('https://github.com/orgs/SRFSC-Organization/projects/1'), { config, fetchImpl: fetchWithAuthors });
      entry.board.cards.forEach((card) => {
        card.ownerKind = 'Assigned to';
        if (!card.people.length && authors.has(card.url)) {
          card.people = [authors.get(card.url)];
          card.ownerKind = 'Created by';
        }
      });
      board = entry.board;
      writeEntry(cacheKey, entry);
      render();
      status.hidden = true;
    } catch (error) {
      status.hidden = false;
      status.textContent = `${board ? 'Showing the saved board. ' : ''}Unable to refresh from GitHub. ${error.message}`;
    }
  }
  loadBoard();
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
  /* This page owns its board presentation; shared styles and scripts stay untouched. */
  #srfsc-board {
    box-sizing: border-box;
    margin: 1.5rem 0 2rem;
    padding: 16px;
    background: #292929;
    font-family: system-ui, sans-serif;
    font-size: 16px;
    color: #e6edf3 !important;
  }
  #srfsc-board * { box-sizing: border-box; }
  #srfsc-board .srfsc-board-toolbar,
  #srfsc-board .srfsc-team-filters {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
  }
  #srfsc-board .srfsc-board-toolbar { margin-bottom: 16px; }
  #srfsc-board .srfsc-team-label { color: #ababab !important; font-size: 18px; }
  #srfsc-board .srfsc-team-button {
    appearance: none;
    padding: 6px 12px;
    border: 0;
    border-radius: 999px !important;
    background: #1b2230;
    color: #3b82f6 !important;
    font: inherit;
    font-size: 17px;
    line-height: 1.3;
    cursor: pointer;
  }
  #srfsc-board .srfsc-team-button[aria-pressed="true"] { background: #162b4b; color: #e6edf3 !important; }
  #srfsc-board .srfsc-team-button:hover { background: #233651; }
  #srfsc-board .srfsc-backlog-toggle { display: inline-flex; align-items: center; gap: 10px; cursor: pointer; }
  #srfsc-board .srfsc-backlog-toggle input { position: absolute; width: 1px; height: 1px; opacity: 0; }
  #srfsc-board .srfsc-backlog-label { font-size: 18px; color: #e6edf3 !important; }
  #srfsc-board .srfsc-toggle-track { position: relative; width: 54px; height: 32px; border-radius: 32px; border: 1px solid #333; background: #252525; }
  #srfsc-board .srfsc-toggle-track::before { content: ""; position: absolute; width: 24px; height: 24px; top: 3px; left: 3px; border-radius: 50%; background: #e6edf3; transition: transform 0.15s ease; }
  #srfsc-board input:checked + .srfsc-toggle-track { background: #2563eb; }
  #srfsc-board input:checked + .srfsc-toggle-track::before { transform: translateX(22px); }
  #srfsc-board input:focus-visible + .srfsc-toggle-track,
  #srfsc-board a:focus-visible,
  #srfsc-board button:focus-visible { outline: 2px solid #60a5fa; outline-offset: 3px; }
  #srfsc-board .ocs__kanban-board {
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: minmax(250px, 1fr);
    align-items: stretch;
    gap: 14px;
    margin: 0;
    padding: 0 0 6px;
    list-style: none;
    overflow-x: auto;
    overscroll-behavior-x: contain;
    scroll-snap-type: x proximity;
    scrollbar-color: #515151 #292929;
  }
  #srfsc-board .ocs__kanban-column {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    justify-content: flex-start;
    min-width: 0;
    min-height: 760px;
    gap: 14px;
    margin: 0;
    padding: 14px;
    border: 1px solid #393939;
    border-top: 3px solid #3b82f6;
    border-radius: 14px;
    background: #303030;
    color: #e6edf3 !important;
    scroll-snap-align: start;
  }
  #srfsc-board .ocs__kanban-column[data-stage="todo"] { border-top-color: #5878a2; }
  #srfsc-board .srfsc-column-heading { display: flex; align-items: center; gap: 7px; min-height: 32px; margin-bottom: 2px; color: #e6edf3 !important; }
  #srfsc-board .srfsc-column-heading strong { font-size: 20px; font-weight: 750; }
  #srfsc-board .ocs__status-pill,
  #srfsc-board .srfsc-more { width: fit-content; padding: 3px 9px; border: 1px solid #3a3a3a; border-radius: 999px !important; background: #2c2c2c; color: #ababab !important; font: inherit; font-size: 13px; font-weight: 600; line-height: 1.4; }
  #srfsc-board .srfsc-more { cursor: pointer; }
  #srfsc-board .srfsc-more:hover { border-color: #64748b; color: #e6edf3 !important; }
  #srfsc-board .ocs__kanban-item { display: grid; gap: 4px; margin: 0; padding: 13px; border: 1px solid #363636; border-radius: 12px; background: #292929; text-decoration: none; text-align: left; box-shadow: none; overflow-wrap: anywhere; }
  #srfsc-board .ocs__kanban-item:hover,
  #srfsc-board .ocs__kanban-item:focus-visible { background: #292929; border-color: #3b82f6; text-decoration: none; transform: none; }
  #srfsc-board .ocs__kanban-kicker { font-size: 12px; line-height: 1.4; font-weight: 700; letter-spacing: 0.035em; text-transform: uppercase; color: #ababab !important; }
  #srfsc-board .ocs__kanban-name { font-size: 18px; line-height: 1.35; font-weight: 700; color: #e6edf3 !important; }
  #srfsc-board .ocs__kanban-note { font-size: 16px; line-height: 1.4; color: #ababab !important; }
  #srfsc-board .ocs__kanban-evidence { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 4px; }
  #srfsc-board .srfsc-empty-column { color: #ababab !important; font-size: 14px; }
  #srfsc-board .srfsc-board-footer { display: flex; flex-wrap: wrap; justify-content: space-between; gap: 12px; padding-top: 12px; font-size: 12px; }
  #srfsc-board .srfsc-board-meta,
  #srfsc-board .srfsc-board-status { color: #ababab !important; }
  #srfsc-board .srfsc-board-footer a { color: #60a5fa; }
  #srfsc-board [hidden] { display: none !important; }
  @media (min-width: 1200px) {
    #srfsc-board { position: relative; left: 50%; width: calc(100vw - 48px); max-width: none; transform: translateX(-50%); }
  }
  @media (max-width: 600px) {
    #srfsc-board { padding: 10px; }
    #srfsc-board .ocs__kanban-board { grid-auto-columns: 88%; gap: 10px; }
    #srfsc-board .ocs__kanban-column { min-height: 580px; padding: 12px; }
    #srfsc-board .srfsc-board-toolbar { gap: 12px; }
    #srfsc-board .srfsc-team-filters { gap: 8px; }
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
