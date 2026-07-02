# Personal Website Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Redesign Alfonso Puicercus' personal website into a compact portfolio that presents his CERN detector R&D, side projects, and personal interests in one polished static page.

**Architecture:** Keep the existing static GitHub Pages structure with `index.html` and `style.css`. Replace the current narrow résumé page with semantic sections, reusable CSS component patterns, responsive grids, and static manually curated project content. No runtime data fetching or JavaScript is needed.

**Tech Stack:** Plain HTML5, CSS3, GitHub Pages, Google Fonts with system fallbacks.

## Global Constraints

- Keep the site as plain HTML + CSS with no framework and no JavaScript.
- Keep the initial redesign to `index.html` and `style.css`; do not add image assets.
- Use a 1080px responsive max-width layout.
- Preserve public links to GitHub, LinkedIn, and email.
- Include research lines for TCAD device simulation, Garfield++ signal modelling, and sensor characterisation/test-beam context.
- Include selected work for TREDI 2026, JINST proceedings, TCAD simulation suite, and Velopix characterisation.
- Include side projects for Physim, SourceRelay, Groundstation, Claude Monitor, and a short supporting mention of Raspberry Pi/personal dashboard systems.
- Include a public, compact outside-lab section mentioning drawing/art, manga/books, films/games, and self-hosting/personal systems.
- Avoid private vault details, credentials, logistics, or addresses.
- Avoid client-side GitHub API calls.
- Ensure semantic landmarks, one clear `h1`, logical heading order, visible focus states, sufficient contrast, and no mobile horizontal overflow.

---

### Task 1: Replace Page Content And Structure

**Files:**
- Modify: `/Users/alfonso/Desktop/alfonsopuicercus.github.io/index.html`

**Interfaces:**
- Consumes: Approved design spec at `/Users/alfonso/Desktop/alfonsopuicercus.github.io/docs/superpowers/specs/2026-07-02-personal-website-redesign-design.md`.
- Produces: Semantic HTML sections and class names consumed by `style.css`: `site-shell`, `site-hero`, `hero-grid`, `eyebrow`, `hero-actions`, `signal-card`, `section-heading`, `research-grid`, `research-line`, `work-list`, `work-card`, `project-grid`, `project-card`, `tag-list`, `interest-grid`, `interest-card`, `contact-panel`, `site-footer`.

- [ ] **Step 1: Replace `index.html` with the full semantic page**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Alfonso Puicercus — CERN PhD student working on fast 3D silicon sensors, physics simulations, and small tools for making complex systems usable." />
  <title>Alfonso Puicercus</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="site-shell">
    <header class="site-hero">
      <nav class="topbar" aria-label="Primary navigation">
        <a class="brand" href="#top" aria-label="Alfonso Puicercus home">AP</a>
        <div class="nav-links">
          <a href="#research">Research</a>
          <a href="#projects">Projects</a>
          <a href="#outside">Outside</a>
          <a href="#contact">Contact</a>
        </div>
      </nav>

      <div class="hero-grid" id="top">
        <div class="hero-copy">
          <p class="eyebrow">CERN · LHCb VELO Upgrade 2 · Fast silicon sensors</p>
          <h1>Alfonso Puicercus</h1>
          <p class="hero-title">PhD student building timing-aware detector simulations and small tools that make complicated systems easier to use.</p>
          <p class="hero-text">My research sits between 3D silicon sensor design, TCAD electric-field simulation, Garfield++ signal modelling, and the experimental reality of characterisation and test beams. Outside the lab, I like building physics simulations, personal automation systems, and things that turn messy workflows into something you can actually touch.</p>
          <div class="hero-actions" aria-label="Primary links">
            <a href="https://github.com/alfonsopuicercus" target="_blank" rel="noopener">GitHub</a>
            <a href="https://ch.linkedin.com/in/alfonso-puicercus" target="_blank" rel="noopener">LinkedIn</a>
            <a href="mailto:alfonso.puicercus@gmail.com">Email</a>
          </div>
        </div>

        <aside class="signal-card" aria-label="Research snapshot">
          <span class="signal-line" aria-hidden="true"></span>
          <p class="signal-label">Current focus</p>
          <h2>Fast 3D sensors for high-rate particle tracking</h2>
          <p>Predicting how geometry, fields, and charge transport shape the timing response of silicon detectors before devices are manufactured and tested.</p>
          <dl class="signal-facts">
            <div>
              <dt>Tools</dt>
              <dd>TCAD · Garfield++ · Python</dd>
            </div>
            <div>
              <dt>Context</dt>
              <dd>LHCb · VELO · CERN EP R&amp;D</dd>
            </div>
          </dl>
        </aside>
      </div>
    </header>

    <main>
      <section class="section research-lines" id="research">
        <div class="section-heading">
          <p class="eyebrow">Research lines</p>
          <h2>From sensor geometry to induced signal.</h2>
          <p>I work on the chain that connects a proposed 3D silicon sensor design to the signal a particle would leave in a future vertex detector.</p>
        </div>

        <div class="research-grid">
          <article class="research-line">
            <span class="line-index">01</span>
            <h3>TCAD device simulation</h3>
            <p>Parametrised 3D sensor models, electric-field maps, depletion behaviour, and charge collection studies for candidate geometries.</p>
          </article>
          <article class="research-line">
            <span class="line-index">02</span>
            <h3>Garfield++ signal modelling</h3>
            <p>Transporting charge through simulated fields to estimate induced current, timing response, and spatial performance before fabrication.</p>
          </article>
          <article class="research-line">
            <span class="line-index">03</span>
            <h3>Characterisation context</h3>
            <p>Connecting simulation assumptions to OPTIMA, Timepix4, laser and test-beam work, and production discussions with sensor partners.</p>
          </article>
        </div>
      </section>

      <section class="section selected-work">
        <div class="section-heading">
          <p class="eyebrow">Selected work</p>
          <h2>Detector R&amp;D, papers, and simulation infrastructure.</h2>
        </div>

        <div class="work-list">
          <article class="work-card">
            <div>
              <p class="work-meta">Presented · TREDI 2026</p>
              <h3>Fast 3D Silicon Sensors for LHCb VELO Upgrade II</h3>
            </div>
            <p>Poster work on simulation-driven development of 3D silicon sensors for the timing requirements of a future LHCb vertex detector.</p>
          </article>
          <article class="work-card">
            <div>
              <p class="work-meta">In preparation · JINST proceedings</p>
              <h3>Simulation results for fast 3D sensor studies</h3>
            </div>
            <p>Proceedings contribution gathering current TCAD and Garfield++ results from the TREDI work.</p>
          </article>
          <article class="work-card">
            <div>
              <p class="work-meta">Ongoing · TCAD / Garfield++</p>
              <h3>3D sensor simulation suite</h3>
            </div>
            <p>Parametrised device models, field extraction, and downstream signal simulations for comparing sensor layouts and operating conditions.</p>
          </article>
          <article class="work-card">
            <div>
              <p class="work-meta">Previous work · Velopix</p>
              <h3>Velopix detector characterisation</h3>
            </div>
            <p>Analysis framework and detector characterisation work from my master's thesis, connecting measured behaviour to physical parameters.</p>
          </article>
        </div>
      </section>

      <section class="section built-projects" id="projects">
        <div class="section-heading">
          <p class="eyebrow">Built for curiosity</p>
          <h2>Side projects where physics, automation, and personal systems meet.</h2>
          <p>Most of my projects start from the same itch: make an abstract system visible, controllable, or easier to reason about.</p>
        </div>

        <div class="project-grid">
          <article class="project-card featured">
            <div class="project-topline">
              <h3><a href="https://github.com/alfonsopuicercus/physicslab" target="_blank" rel="noopener">Physim</a></h3>
              <span>Physics simulations</span>
            </div>
            <p>Interactive browser simulations paired with Physim Lab, a Python desktop framework for research-grade models and shared `.physim` scenarios.</p>
            <div class="tag-list" aria-label="Physim stack">
              <span>HTML/CSS/JS</span>
              <span>Python</span>
              <span>Cloudflare</span>
            </div>
          </article>

          <article class="project-card">
            <div class="project-topline">
              <h3><a href="https://github.com/alfonsopuicercus/source-relay" target="_blank" rel="noopener">SourceRelay</a></h3>
              <span>Personal data bridge</span>
            </div>
            <p>A local macOS bridge that turns Calendar, Things 3, and Obsidian into one clean API for personal dashboards.</p>
            <div class="tag-list" aria-label="SourceRelay stack">
              <span>Swift</span>
              <span>macOS</span>
            </div>
          </article>

          <article class="project-card">
            <div class="project-topline">
              <h3><a href="https://github.com/alfonsopuicercus/groundstation" target="_blank" rel="noopener">Groundstation</a></h3>
              <span>Automation</span>
            </div>
            <p>A plugin-based Telegram command centre for system monitoring, local LLM control, job automation, and notifications.</p>
            <div class="tag-list" aria-label="Groundstation stack">
              <span>Python</span>
              <span>Telegram</span>
              <span>Ollama</span>
            </div>
          </article>

          <article class="project-card">
            <div class="project-topline">
              <h3><a href="https://github.com/alfonsopuicercus/claude-monitor" target="_blank" rel="noopener">Claude Monitor</a></h3>
              <span>macOS utility</span>
            </div>
            <p>A Dynamic Island-style overlay for Claude Code sessions, built as a small native utility for keeping agent work visible.</p>
            <div class="tag-list" aria-label="Claude Monitor stack">
              <span>Swift</span>
              <span>macOS</span>
            </div>
          </article>
        </div>

        <p class="supporting-note">I also keep a Raspberry Pi dashboard and home-lab tools around for live personal data, local services, and small experiments in self-hosting.</p>
      </section>

      <section class="section outside-lab" id="outside">
        <div class="section-heading">
          <p class="eyebrow">Outside the lab</p>
          <h2>Things I keep coming back to.</h2>
        </div>

        <div class="interest-grid">
          <article class="interest-card">
            <h3>Drawing and visual ideas</h3>
            <p>Small sketches, comic-like characters, manga-inspired studies, and turning visual references into something handmade.</p>
          </article>
          <article class="interest-card">
            <h3>Books, manga, and films</h3>
            <p>Science fiction, physics books, Vinland Saga, Vagabond, Dune, Perfect Days, Tenet, and stories that make craft feel visible.</p>
          </article>
          <article class="interest-card">
            <h3>Games and systems</h3>
            <p>Strategy games, old Zelda and Pokémon, retro handhelds, self-hosted dashboards, and the pleasing machinery of personal tools.</p>
          </article>
        </div>
      </section>

      <section class="section contact" id="contact">
        <div class="contact-panel">
          <div>
            <p class="eyebrow">Contact</p>
            <h2>Say hello.</h2>
            <p>Reach out about silicon sensors, detector simulations, physics tools, or small systems that make research life easier.</p>
          </div>
          <div class="contact-links" aria-label="Contact links">
            <a href="mailto:alfonso.puicercus@gmail.com">alfonso.puicercus@gmail.com</a>
            <a href="https://github.com/alfonsopuicercus" target="_blank" rel="noopener">GitHub</a>
            <a href="https://ch.linkedin.com/in/alfonso-puicercus" target="_blank" rel="noopener">LinkedIn</a>
          </div>
        </div>
      </section>
    </main>
  </div>

  <footer class="site-footer">
    <div class="footer-inner">
      <span>Alfonso Puicercus</span>
      <span>CERN · 2026</span>
    </div>
  </footer>
</body>
</html>
```

- [ ] **Step 2: Check HTML for required public links**

Run: `rg -n "github.com/alfonsopuicercus|linkedin|mailto|physicslab|source-relay|groundstation|claude-monitor" index.html`

Expected: output includes the GitHub profile, LinkedIn, email, and four project links.

- [ ] **Step 3: Commit markup**

```bash
git add index.html
git commit -m "feat: restructure personal website content"
```

### Task 2: Implement Visual System And Responsive Styling

**Files:**
- Modify: `/Users/alfonso/Desktop/alfonsopuicercus.github.io/style.css`

**Interfaces:**
- Consumes: Class names produced by Task 1.
- Produces: Finished static visual system with 1080px layout, signal trace motif, responsive grids, hover/focus states, and mobile-safe typography.

- [ ] **Step 1: Replace `style.css` with the full stylesheet**

```css
:root {
  --bg: #f8fafc;
  --surface: #ffffff;
  --surface-strong: #eef6fb;
  --text: #142033;
  --muted: #5c687a;
  --soft: #d9e2ec;
  --line: #cbd7e3;
  --blue: #173d6d;
  --cyan: #1ba8c8;
  --warm: #c46a3a;
  --warm-soft: #fff1e8;
  --shadow: 0 18px 55px rgba(23, 61, 109, 0.1);
  --radius: 8px;
  --mono: "IBM Plex Mono", ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
  --sans: "IBM Plex Sans", system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

*, *::before, *::after {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family: var(--sans);
  font-size: 16px;
  line-height: 1.65;
  color: var(--text);
  background:
    linear-gradient(90deg, rgba(23, 61, 109, 0.045) 1px, transparent 1px),
    linear-gradient(180deg, #ffffff 0%, var(--bg) 42%, #f6f8fb 100%);
  background-size: 72px 72px, auto;
}

a {
  color: inherit;
}

a:focus-visible {
  outline: 3px solid rgba(27, 168, 200, 0.55);
  outline-offset: 4px;
  border-radius: 4px;
}

.site-shell {
  width: min(1080px, calc(100% - 40px));
  margin: 0 auto;
}

.topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  padding: 28px 0;
  font-family: var(--mono);
  font-size: 0.78rem;
}

.brand {
  display: inline-grid;
  width: 38px;
  height: 38px;
  place-items: center;
  color: #fff;
  background: var(--blue);
  border-radius: 50%;
  font-weight: 600;
  text-decoration: none;
  box-shadow: 0 10px 24px rgba(23, 61, 109, 0.18);
}

.nav-links {
  display: flex;
  gap: 18px;
  flex-wrap: wrap;
  justify-content: flex-end;
}

.nav-links a {
  color: var(--muted);
  text-decoration: none;
}

.nav-links a:hover {
  color: var(--blue);
}

.site-hero {
  padding-bottom: 72px;
}

.hero-grid {
  display: grid;
  grid-template-columns: minmax(0, 1.45fr) minmax(320px, 0.75fr);
  gap: 48px;
  align-items: stretch;
  min-height: 620px;
  padding: 72px 0 24px;
}

.hero-copy {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.eyebrow {
  margin: 0 0 14px;
  font-family: var(--mono);
  font-size: 0.76rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--blue);
}

h1, h2, h3, p {
  margin-top: 0;
}

h1 {
  max-width: 760px;
  margin-bottom: 18px;
  font-size: 4.6rem;
  line-height: 0.95;
  letter-spacing: 0;
  color: var(--text);
}

.hero-title {
  max-width: 760px;
  margin-bottom: 20px;
  font-size: 1.45rem;
  line-height: 1.35;
  font-weight: 500;
  color: var(--blue);
}

.hero-text {
  max-width: 720px;
  margin-bottom: 32px;
  color: var(--muted);
  font-size: 1.04rem;
}

.hero-actions,
.contact-links {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

.hero-actions a,
.contact-links a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 42px;
  padding: 9px 14px;
  border: 1px solid var(--line);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.75);
  color: var(--blue);
  font-family: var(--mono);
  font-size: 0.82rem;
  font-weight: 500;
  text-decoration: none;
  transition: transform 160ms ease, border-color 160ms ease, background 160ms ease;
}

.hero-actions a:hover,
.contact-links a:hover {
  transform: translateY(-2px);
  border-color: var(--cyan);
  background: #fff;
}

.signal-card {
  position: relative;
  align-self: center;
  min-height: 430px;
  padding: 34px;
  overflow: hidden;
  border: 1px solid rgba(23, 61, 109, 0.16);
  border-radius: var(--radius);
  background:
    radial-gradient(circle at 84% 16%, rgba(27, 168, 200, 0.2), transparent 28%),
    linear-gradient(145deg, #ffffff 0%, #f2f8fc 100%);
  box-shadow: var(--shadow);
}

.signal-card::after {
  content: "";
  position: absolute;
  inset: auto -12% 34px 16%;
  height: 82px;
  background:
    linear-gradient(90deg, transparent 0 8%, var(--cyan) 8% 10%, transparent 10% 26%, var(--cyan) 26% 29%, transparent 29% 48%, var(--warm) 48% 50%, transparent 50% 100%);
  opacity: 0.35;
  clip-path: polygon(0 58%, 12% 58%, 18% 28%, 27% 78%, 36% 42%, 47% 42%, 52% 16%, 61% 70%, 72% 38%, 100% 38%, 100% 44%, 74% 44%, 61% 82%, 51% 28%, 48% 50%, 38% 50%, 27% 88%, 18% 42%, 14% 64%, 0 64%);
}

.signal-line {
  display: block;
  width: 72px;
  height: 3px;
  margin-bottom: 54px;
  background: linear-gradient(90deg, var(--blue), var(--cyan), var(--warm));
}

.signal-label,
.work-meta,
.project-topline span {
  margin: 0 0 10px;
  font-family: var(--mono);
  font-size: 0.74rem;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: var(--warm);
}

.signal-card h2 {
  margin-bottom: 16px;
  font-size: 1.65rem;
  line-height: 1.15;
  color: var(--blue);
}

.signal-card p {
  color: var(--muted);
}

.signal-facts {
  display: grid;
  gap: 18px;
  margin: 36px 0 0;
}

.signal-facts div {
  padding-top: 14px;
  border-top: 1px solid var(--line);
}

.signal-facts dt {
  font-family: var(--mono);
  font-size: 0.72rem;
  color: var(--muted);
  text-transform: uppercase;
}

.signal-facts dd {
  margin: 4px 0 0;
  font-weight: 600;
}

.section {
  padding: 86px 0;
  border-top: 1px solid var(--line);
}

.section-heading {
  max-width: 760px;
  margin-bottom: 34px;
}

.section-heading h2,
.contact-panel h2 {
  margin-bottom: 14px;
  font-size: 2.35rem;
  line-height: 1.08;
  letter-spacing: 0;
}

.section-heading p:not(.eyebrow),
.contact-panel p:not(.eyebrow) {
  color: var(--muted);
  font-size: 1.02rem;
}

.research-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 18px;
}

.research-line,
.project-card,
.interest-card {
  border: 1px solid var(--line);
  border-radius: var(--radius);
  background: rgba(255, 255, 255, 0.82);
}

.research-line {
  min-height: 260px;
  padding: 24px;
}

.line-index {
  display: inline-block;
  margin-bottom: 54px;
  font-family: var(--mono);
  font-size: 0.78rem;
  color: var(--cyan);
}

.research-line h3,
.project-card h3,
.interest-card h3,
.work-card h3 {
  margin-bottom: 10px;
  font-size: 1.12rem;
  line-height: 1.25;
}

.research-line p,
.project-card p,
.interest-card p,
.work-card p,
.supporting-note {
  margin-bottom: 0;
  color: var(--muted);
}

.work-list {
  display: grid;
  gap: 14px;
}

.work-card {
  display: grid;
  grid-template-columns: minmax(260px, 0.9fr) minmax(0, 1.1fr);
  gap: 24px;
  padding: 22px 0;
  border-top: 1px solid rgba(203, 215, 227, 0.9);
}

.work-card:first-child {
  border-top-color: var(--blue);
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 18px;
}

.project-card {
  display: flex;
  min-height: 260px;
  flex-direction: column;
  justify-content: space-between;
  padding: 24px;
  box-shadow: 0 8px 28px rgba(20, 32, 51, 0.04);
}

.project-card.featured {
  background:
    linear-gradient(135deg, rgba(23, 61, 109, 0.94), rgba(22, 92, 128, 0.9)),
    var(--blue);
  color: #fff;
}

.project-card.featured p,
.project-card.featured .project-topline span {
  color: rgba(255, 255, 255, 0.76);
}

.project-card h3 a {
  color: inherit;
  text-decoration: none;
}

.project-card h3 a:hover {
  text-decoration: underline;
  text-decoration-thickness: 2px;
  text-underline-offset: 4px;
}

.project-topline {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  align-items: flex-start;
  margin-bottom: 18px;
}

.project-topline span {
  max-width: 120px;
  text-align: right;
  color: var(--warm);
}

.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 22px;
}

.tag-list span {
  padding: 5px 9px;
  border: 1px solid rgba(203, 215, 227, 0.9);
  border-radius: 999px;
  font-family: var(--mono);
  font-size: 0.72rem;
  color: var(--blue);
  background: #fff;
}

.featured .tag-list span {
  border-color: rgba(255, 255, 255, 0.25);
  color: #fff;
  background: rgba(255, 255, 255, 0.1);
}

.supporting-note {
  max-width: 760px;
  margin-top: 22px;
  padding-left: 18px;
  border-left: 3px solid var(--warm);
}

.interest-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 18px;
}

.interest-card {
  padding: 22px;
  background: linear-gradient(180deg, #fff 0%, var(--warm-soft) 180%);
}

.contact-panel {
  display: grid;
  grid-template-columns: minmax(0, 1fr) auto;
  gap: 32px;
  align-items: center;
  padding: 34px;
  border: 1px solid var(--line);
  border-radius: var(--radius);
  background: #fff;
  box-shadow: var(--shadow);
}

.contact-links {
  justify-content: flex-end;
}

.site-footer {
  border-top: 1px solid var(--line);
  color: var(--muted);
}

.footer-inner {
  display: flex;
  width: min(1080px, calc(100% - 40px));
  margin: 0 auto;
  padding: 24px 0;
  justify-content: space-between;
  gap: 16px;
  font-family: var(--mono);
  font-size: 0.78rem;
}

@media (max-width: 860px) {
  .hero-grid,
  .research-grid,
  .project-grid,
  .interest-grid,
  .contact-panel {
    grid-template-columns: 1fr;
  }

  .hero-grid {
    min-height: auto;
    padding-top: 48px;
  }

  h1 {
    font-size: 3.35rem;
  }

  .signal-card {
    min-height: 360px;
  }

  .work-card {
    grid-template-columns: 1fr;
    gap: 6px;
  }

  .contact-links {
    justify-content: flex-start;
  }
}

@media (max-width: 560px) {
  .site-shell,
  .footer-inner {
    width: min(100% - 28px, 1080px);
  }

  .topbar {
    align-items: flex-start;
    flex-direction: column;
  }

  .nav-links {
    justify-content: flex-start;
    gap: 12px;
  }

  .site-hero {
    padding-bottom: 44px;
  }

  .hero-grid {
    gap: 28px;
    padding-top: 32px;
  }

  h1 {
    font-size: 2.7rem;
  }

  .hero-title {
    font-size: 1.18rem;
  }

  .section {
    padding: 58px 0;
  }

  .section-heading h2,
  .contact-panel h2 {
    font-size: 1.9rem;
  }

  .signal-card,
  .research-line,
  .project-card,
  .interest-card,
  .contact-panel {
    padding: 20px;
  }

  .project-topline {
    flex-direction: column;
    gap: 4px;
  }

  .project-topline span {
    max-width: none;
    text-align: left;
  }

  .footer-inner {
    flex-direction: column;
  }
}
```

- [ ] **Step 2: Check CSS for prohibited viewport font scaling and obvious one-note palette**

Run: `rg -n "vw|vh|#|--blue|--cyan|--warm" style.css`

Expected: no `vw` font sizes; palette includes blue, cyan, and warm accent variables.

- [ ] **Step 3: Commit styling**

```bash
git add style.css
git commit -m "feat: restyle personal website"
```

### Task 3: Local Verification And Polish

**Files:**
- Modify if needed after inspection: `/Users/alfonso/Desktop/alfonsopuicercus.github.io/index.html`
- Modify if needed after inspection: `/Users/alfonso/Desktop/alfonsopuicercus.github.io/style.css`

**Interfaces:**
- Consumes: Implemented static page from Tasks 1 and 2.
- Produces: Verified responsive page with no obvious content, layout, or accessibility regressions.

- [ ] **Step 1: Run local static server**

Run: `python3 -m http.server 8000`

Expected: server prints `Serving HTTP on :: port 8000` or equivalent.

- [ ] **Step 2: Verify page loads**

Open: `http://127.0.0.1:8000`

Expected: page renders with hero, research, selected work, projects, outside-lab, contact, and footer.

- [ ] **Step 3: Capture desktop screenshot**

Use a 1280px-wide browser viewport and capture a screenshot.

Expected: hero has no clipped content, signal card is visible, next section is reachable by scroll, links are visible.

- [ ] **Step 4: Capture mobile screenshot**

Use a 390px-wide browser viewport and capture a screenshot.

Expected: no horizontal overflow, nav wraps cleanly, cards stack, project labels do not collide with titles, contact links wrap.

- [ ] **Step 5: Check external links in source**

Run: `rg -n "target=\"_blank\" rel=\"noopener\"" index.html`

Expected: all external non-mail links use `target="_blank" rel="noopener"`.

- [ ] **Step 6: Run a lightweight text and file sanity check**

Run: `python3 - <<'PY'\nfrom pathlib import Path\nhtml = Path('index.html').read_text()\ncss = Path('style.css').read_text()\nrequired = ['TCAD', 'Garfield++', 'Physim', 'SourceRelay', 'Groundstation', 'Claude Monitor', 'drawing', 'manga', 'GitHub', 'LinkedIn']\nmissing = [item for item in required if item not in html]\nassert not missing, missing\nassert 'font-size: 4.6rem' in css\nassert 'width: min(1080px' in css\nprint('static sanity checks passed')\nPY`

Expected: `static sanity checks passed`.

- [ ] **Step 7: Apply targeted fixes if screenshots show issues**

Only edit the specific rule or markup causing a visible issue. Do not add new sections, JavaScript, or assets.

- [ ] **Step 8: Commit verification fixes if any**

If files changed:

```bash
git add index.html style.css
git commit -m "fix: polish personal website layout"
```

If no files changed, do not create an empty commit.

