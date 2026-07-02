# Personal Website Redesign Design

Date: 2026-07-02
Repo: `alfonsopuicercus/alfonsopuicercus.github.io`
Live site: `https://alfonsopuicercus.github.io`

## Goal

Improve Alfonso Puicercus' personal website so it reads less like a short academic profile and more like a compact personal portfolio: a CERN PhD student developing fast 3D silicon sensors, and a curious builder of physics simulations, personal infrastructure, automation tools, and small systems.

The site should remain a fast, static GitHub Pages site using plain HTML and CSS. No framework or JavaScript is required for this redesign.

## Audience

- Research collaborators, supervisors, conference readers, and detector R&D people who need to understand Alfonso's main research lines quickly.
- Technical visitors from GitHub who want to understand the side projects and tooling.
- Friends, future collaborators, and curious readers who should get a small but real sense of Alfonso's interests outside the lab.

## Core Thesis

Alfonso develops fast silicon sensors for high-energy physics, and also builds simulations, tools, and personal systems because he likes making complex things tangible and usable.

## Information Architecture

The page remains one static page with anchored sections.

1. Hero
   - Name: Alfonso Puicercus.
   - Role: PhD student at CERN.
   - Main line: fast 3D silicon sensors for LHCb VELO Upgrade 2.
   - Primary links: GitHub, LinkedIn, Email.
   - Tone: direct, clear, personal, not over-sold.

2. Research Lines
   - Three compact tracks:
     - TCAD device simulation: modelling electric fields, depletion, geometry, and charge collection in 3D sensors.
     - Garfield++ signal modelling: turning device fields into particle-response and timing predictions.
     - Sensor characterisation and test-beam context: connecting simulation to OPTIMA, Timepix4, laser/test-beam work, and production partners.
   - This section should explain the research in plain language while retaining the correct technical terms.

3. Selected Work
   - TREDI 2026 poster: Fast 3D Silicon Sensors for LHCb VELO Upgrade II.
   - JINST proceedings paper: in preparation or updated if status changes during implementation.
   - TCAD simulation suite: parametrised 3D geometry, field extraction, Garfield++ integration.
   - Velopix characterisation: previous master's thesis / detector characterisation work.

4. Built For Curiosity
   - A project section for GitHub and side projects.
   - Include a balanced subset, prioritised as:
     - Physim / physicslab: interactive physics simulations and research-grade Physim Lab.
     - SourceRelay: local macOS bridge for Calendar, Things 3, and Obsidian dashboards.
     - Groundstation: Telegram command centre for system monitoring, local LLM control, and automation.
     - Claude Monitor: Dynamic Island-style macOS overlay for Claude Code sessions.
     - Personal dashboard / Raspberry Pi systems as a short supporting mention, not a full project card.
   - Each item should have a short description, language/stack where useful, and a link.

5. Outside The Lab
   - A human section, not a résumé dump.
   - Mention drawing/art, manga/books, films/games, and self-hosting/personal systems.
   - Keep this public and non-invasive: no private logistics, addresses, credentials, or overly personal notes.
   - The section should make Alfonso feel like a real person without distracting from the professional core.

6. Contact
   - Keep concise: email, GitHub, LinkedIn.
   - Invite contact about sensors, simulations, tools, or physics projects.

## Visual Direction

The design should feel like a "lab notebook meets personal workshop":

- Clean, precise, and technical enough for a research audience.
- Warmer and more dimensional than the current narrow text page.
- Lightweight and static, with no heavy animation or framework dependency.

## Design System

### Palette

- Background: near-white, not beige.
- Text: graphite/near-black.
- Muted text: cool gray.
- Primary accent: deep CERN-like blue.
- Technical accent: silicon/electric-field cyan.
- Personal accent: a restrained warm amber or coral used sparingly for side projects and outside-lab details.

Avoid a one-note blue site. The warm accent should help distinguish Alfonso's personal/building side from the research side.

### Typography

- Body/UI: a highly readable sans-serif.
- Section labels and project metadata: slightly technical, compact, and disciplined.
- Headings: stronger and more characterful than the current site, but still professional.
- Do not use viewport-width font scaling. Mobile typography should be explicitly sized with media queries.

### Layout

- Wider than the current 720px text column, with a responsive max width of 1080px.
- Hero should be left-aligned and spacious, with enough information above the fold to establish identity and research.
- Research lines can use a three-column layout on desktop and stacked blocks on mobile.
- Projects should be compact rows or cards with stable spacing, not a repetitive oversized card grid.
- Outside-lab items can feel like a small shelf of interests, using short labels and concise prose.
- Use cards only for repeated items. Do not nest cards inside cards.

### Signature Element

Use a subtle "signal trace" motif inspired by detector waveforms, induced signals, or electric-field paths:

- Thin line dividers or small inline accents.
- Used sparingly between major sections or beside headings.
- Implemented in CSS, not as decorative clutter.

## Content Style

- Research copy should be technically accurate but readable for a motivated non-specialist.
- Project copy should be specific about what each project does without sounding like startup marketing.
- Personal copy should be warm, compact, and public.
- Avoid generic claims like "passionate about innovation".
- Avoid private details from the vault.

## Implementation Architecture

The existing site has two files:

- `index.html`
- `style.css`

The initial redesign should keep this two-file structure and avoid adding image assets. If Alfonso later provides a personal photo or specific visual asset, it should be placed under an `assets/` folder and referenced from `index.html`.

Recommended HTML structure:

- `header.site-hero`
- `main`
  - `section.research-lines`
  - `section.selected-work`
  - `section.built-projects`
  - `section.outside-lab`
  - `section.contact`
- `footer.site-footer`

Reusable CSS component families:

- Links/buttons.
- Section headers with signal trace accents.
- Research line panels.
- Work/project cards or rows.
- Metadata tags.
- Interest chips or compact interest blocks.

## Data Flow

There is no runtime data flow. All content is static HTML.

GitHub project data may be copied manually from public repository metadata during implementation. The site should not call the GitHub API client-side.

## Error Handling

Because the site is static, error handling is mostly about graceful degradation:

- External links open in a new tab and use `rel="noopener"`.
- If web fonts fail, system fallbacks should keep the page readable.
- If any future images fail, alt text and layout dimensions should prevent disruptive layout shifts.
- Email link should remain plain `mailto:`.

## Accessibility

- Semantic landmarks: `header`, `main`, `section`, `footer`.
- One clear `h1`; logical heading order.
- Sufficient contrast for all text and link states.
- Visible focus states for links and buttons.
- Mobile layout without horizontal overflow.
- No animation that is required to understand the page.

## Testing And Verification

Implementation should verify:

- The page opens locally in a browser.
- Desktop layout at 1280px width.
- Mobile layout at 390px width.
- No horizontal overflow on mobile.
- Link targets are correct.
- Text does not overlap, clip, or become too small.
- Lighthouse or equivalent basic checks are acceptable if available, but manual visual inspection is required.

## Out Of Scope

- Blog system.
- CMS.
- JavaScript filtering or dynamic GitHub API loading.
- Custom domain setup.
- Private vault/task/dashboard data.
- Editing Things 3 tasks.
- Publishing a new paper status unless Alfonso confirms the current publication state.

## Open Implementation Notes

- Use current known public project links:
  - `https://github.com/alfonsopuicercus`
  - `https://github.com/alfonsopuicercus/physicslab`
  - `https://github.com/alfonsopuicercus/source-relay`
  - `https://github.com/alfonsopuicercus/groundstation`
  - `https://github.com/alfonsopuicercus/claude-monitor`
  - `https://github.com/alfonsopuicercus/calibration_velopix_irradiation`
- Keep the TREDI/JINST wording conservative unless Alfonso provides an updated publication link or status.
