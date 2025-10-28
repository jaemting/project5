## Project overview

This is a small static website (no build tools). Top-level HTML files live in the repository root: `index.html`, `blog.html`, `shop.html`, `concerts.html`. CSS is in `css/style.css`.

AI agent short goal: make safe, minimal edits to HTML/CSS, preserve existing relative links, and prefer non-disruptive UI improvements. There are no server-side components or tests to run.

## Key files & patterns (use these as examples)
- `index.html` — main page. Navigation uses simple relative links (e.g. `<a href="blog.html">blog</a>`). updates should keep these relative links intact.
- `css/style.css` — single stylesheet. Look for classes used in the HTML: `.logo`, `.subheader`, `.images`, `.about-us`, `.general-information`, `.specific-information`. Media queries at 768px and 1024px implement grid layouts for tablet/desktop.

Examples to cite when modifying layout or styles:
- Add small spacing: modify `.logo` or `article` margins in `css/style.css`.
- To change navigation highlight, update the `.highligt` class on the active `<a>` in the HTML and adjust `ul li a` rules in `css/style.css`.

## Developer workflow (how to preview and test changes)
- No build step — open `index.html` directly in a browser to preview local changes.
- For a local server (recommended to avoid cross-file resource issues), use Python or VS Code Live Server:
  - Python (PowerShell): `python -m http.server 8000` then open `http://localhost:8000`.
  - VS Code: install the Live Server extension and use "Open with Live Server".

## Conventions & constraints the agent must follow
- Preserve file-level structure: HTML files remain in the repo root and CSS in `css/`.
- Use only relative paths for assets and links (do not introduce absolute URLs unless required and explicitly approved).
- Keep markup semantic and minimal; prefer adding classes over inline styles when changing presentation.
- Avoid large refactors (no renaming of many files or moving directories) without human sign-off.

## When making changes, include these in commit messages
- Short, imperative: e.g. `fix(nav): correct active link class in index.html` or `style: adjust article spacing in css/style.css`.

## Known missing info / safe defaults
- There is no test harness or CI. Assume manual review by a human after changes.
- If a missing resource (image, font) is referenced, prefer to keep the reference and add a TODO comment in the file rather than removing it.

## Quick examples the agent can use directly
- Change nav active link in `index.html`: add/remove `class="highligt"` on the appropriate `<a>` tag.
- Small CSS tweak: to increase article padding, edit `article { padding: 10px; }` in `css/style.css`.

## If unsure / escalation
- If a change touches multiple pages (navigation, global layout) or moves files, add a short note in the PR description explaining why and request human review.

---
If you want more detail (preferred responsive breakpoints, naming conventions, or workflow automation), tell me which area to expand and I will update this file.
