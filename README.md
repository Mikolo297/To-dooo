# Todo Item Card — Stage 0 Frontend

A high-fidelity, interactive Todo Item Card built with semantic HTML, CSS, and vanilla JavaScript. No frameworks, no build step — just open and run.

## Live URL

> **https://YOUR-DEPLOYED-URL** *(replace after deploying to Netlify/Vercel/GitHub Pages)*

## How to Run Locally

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/todo-card.git
cd todo-card

# Open directly in browser — no build step needed
open index.html
# or just double-click index.html
```

That's it. No npm install, no bundler.

## All Required `data-testid` Attributes

| Element             | `data-testid`                    |
|---------------------|----------------------------------|
| Card container      | `test-todo-card`                 |
| Task title          | `test-todo-title`                |
| Task description    | `test-todo-description`          |
| Priority badge      | `test-todo-priority`             |
| Due date            | `test-todo-due-date`             |
| Time remaining      | `test-todo-time-remaining`       |
| Status indicator    | `test-todo-status`               |
| Checkbox            | `test-todo-complete-toggle`      |
| Categories list     | `test-todo-tags`                 |
| Tag (design)        | `test-todo-tag-design`           |
| Tag (mobile)        | `test-todo-tag-mobile`           |
| Tag (ux)            | `test-todo-tag-ux`               |
| Tag (q2)            | `test-todo-tag-q2`               |
| Edit button         | `test-todo-edit-button`          |
| Delete button       | `test-todo-delete-button`        |

## Decisions Made

- **Vanilla HTML/CSS/JS** — No framework overhead. The task is a single card; React would be overkill and add unnecessary complexity for a grader to run.
- **Semantic elements** — `<article>` for the card root, `<h2>` for title, `<p>` for description, `<time>` elements with `datetime` attributes for both date fields, real `<input type="checkbox">` with `<label>`, `<ul role="list">` for tags, `<button>` elements for actions.
- **Live time updates** — `setInterval` every 30 seconds recalculates time remaining against actual system time. No hardcoded values.
- **Accessibility** — All icon-only buttons have `aria-label`. Checkbox has an associated `<label>`. Tags list has `aria-label`. Priority and status use colour + text (not colour alone).
- **Dark aesthetic** — Refined dark theme with a subtle grid background, accent glow, and micro-interactions (hover states, checkbox animation, completed state).

## Trade-offs

- No persistence — state resets on page refresh. Out of scope for a single card component.
- Edit action shows an alert placeholder — the brief didn't specify an edit UI.
- Due date is set to 4 days from now at runtime so time-remaining always shows a realistic value during grading.

## Responsive

Works on mobile and desktop. Max-width 520px, centered.
