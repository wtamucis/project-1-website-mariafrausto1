## Repo snapshot

- Type: small static website (plain HTML + CSS). No JS, no build tools, no package manager.
- Key files: `index.html`, `petcaretips.html`, `petstories.html`, `styles.css`, and the `images/` folder.
- README.md contains instructor directions and git workflow to follow. Use it as the canonical source for git commands and classroom requirements.

## Immediate goals for an AI contributor

- Make minimal, self-contained edits to HTML/CSS that preserve the existing navigation and file layout.
- Preserve or improve image references so pages load when served from the project root.
- Do not add new tooling or dependencies unless the user explicitly asks.

## Important patterns & gotchas (copy/paste examples)

- Pages are root-level HTML files and link to each other with relative links in the nav. Example: `<a href="petcaretips.html">Pet Care Tips</a>` (see `index.html`).
- Images live in the `images/` folder. README rules expect lowercase filenames and no spaces. Examples of current mismatches you may encounter:
  - `petcaretips.html` uses `images/feeding schedule.jpg` (contains a space).
  - `styles.css` sets `background-image: url("/images/bg-image.png");` (leading `/` makes it root-absolute when served from a server; other pages use `images/...`).
  - Use `images/dog-wash.jpg` and `images/header-image.jpg` as shown in the HTML.

When editing images or paths, prefer consistent relative paths (`images/...`) and lowercase, hyphen-separated filenames to match README guidance and avoid case/space issues on remote servers.

## Dev / preview workflow (discovered in README)

- Preferred quick preview in VS Code: Recommended extension "Live Server" — right click an HTML file and choose "Open with Live Server".
- Minimal CLI alternative (works on Windows PowerShell if Python is installed):

  python -m http.server 8000

  Run that from the project root and open http://localhost:8000 in a browser.

- Git workflow: follow the commands already present in `README.md` (git add -A, commit, push). Do not overwrite or remove the instructor-provided instructions.

## What to change and what to avoid

- Safe: fix broken image paths, remove spaces in filenames (also update the HTML that references them), make small CSS tweaks that don't reorganize the layout, and add alt text to images.
- Avoid: introducing a build tool, renaming many files without user approval, or changing the repository structure (all HTML should remain in the repo root unless the user asks for a refactor).

## Minimal contract for code edits

- Input: edits to HTML/CSS and images in this repo.
- Output: pages remain navigable; images resolve when served from project root; README git instructions remain unchanged.
- Success criteria: after edits, opening `index.html` via Live Server or `python -m http.server` shows the homepage, nav links work, and images load.

## Examples of repo-specific fixes an AI can propose/edit

- Replace `background-image: url("/images/bg-image.png");` with `background-image: url("images/bg-image.png");` to use a relative path (or note why the leading `/` is required).
- Rename `feeding schedule.jpg` -> `feeding-schedule.jpg` (update `petcaretips.html` src accordingly) to follow README filename rules.
- When adding images, place them into `images/` and reference them as `images/<file>`; lowercase and hyphenate names.

## When to ask the user

- If a change requires moving many files, introducing tooling, or changing branch history—ask before proceeding.
- If images are missing from `images/` (not discoverable in the repo), ask whether to remove references or to supply assets.

---
If any part of this guidance is unclear or you want me to make the actual fixes (e.g., rename images and update HTML/CSS), say which changes to make and I'll apply them now.
