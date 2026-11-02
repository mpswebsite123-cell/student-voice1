# StudentVoice — implementation plan

## Scope
A polished Digital Fest demo built with plain HTML, CSS and JavaScript in the frontend. The demo includes a landing page, student portal, agency dashboard, privacy and safety content, fictional samples, simulated routing, client-side validation, and responsive interaction. It does not claim secure authentication or confidential storage.

The current project is initialized with a managed web starter, but the product code intentionally uses only `client/index.html`, `client/src/main.js`, and `client/src/styles.css`. The starter server/database files remain available as scaffolding for a future Python/SQL backend migration, but are not used by the demo.

## Design

### Three candidate styles
- **Civic Signal / editorial public-service interface** — 0.07
- **Soft academic dashboard / friendly campus utility** — 0.06
- **Dark cyber-reporting console** — 0.05

### Chosen direction: Civic Signal
- **Design Movement:** contemporary civic-tech editorial design: trustworthy, calm, spacious, and information-forward.
- **Core Principles:** make privacy visible; pair warmth with operational clarity; use progressive disclosure; make every action feel reversible and understandable.
- **Color Philosophy:** deep ink navy signals seriousness and institutional trust; mineral teal signals care and action; warm paper backgrounds prevent the experience from feeling punitive; coral is reserved for urgent attention.
- **Layout Paradigm:** an asymmetric editorial landing page with a narrow eyebrow rail, oversized headline, floating workflow card, and horizontal evidence bands instead of a generic centered grid.
- **Signature Elements:** teal “signal” linework; rounded status pills; small uppercase micro-labels that make demo/provenance explicit.
- **Interaction Philosophy:** actions explain what happens next. Forms use clear validation, route previews, confirmation states, and non-alarming feedback.
- **Animation:** short ease-out entrances, subtle line drawing and floating card motion; respect `prefers-reduced-motion`.
- **Typography System:** system sans stack for accessibility and speed, with wide uppercase microcopy and high-contrast display sizing. Use weight and spacing, not decorative fonts, for authority.
- **Brand Essence:** a student-first reporting bridge for safer schools; clear, protective, grounded.
- **Brand Voice:** direct and reassuring. Example lines: “Your concern deserves a clear next step.” “This demo shows the flow — not a promise of anonymity.”
- **Wordmark & Logo:** a speech-bubble mark intersected by a small signal line, paired with a compact StudentVoice wordmark.
- **Signature Brand Color:** Signal Teal `#13B8A6`.

## Structure
- `client/index.html`: semantic app shell and metadata.
- `client/src/main.js`: SPA state, rendering, form flows, demo auth, sample data, routing simulation, agency filters, and accessible event handling.
- `client/src/styles.css`: responsive civic-tech visual system, cards, dashboard layouts, modal, status timeline, mobile nav, and reduced-motion rules.
- `client/public/manus-routes.json`: declared page routes for the single-page demo.
- `SETUP.md`: run instructions, demo credentials, honest capability notes, and Python/SQL next steps.

## Backend boundary
For a real deployment, move users, sessions, reports, evidence metadata, audit logs, routing rules, and role checks into Python API endpoints and SQL tables. Student and agency authorization must be enforced server-side; browser state/local storage is never represented as secure authentication.
