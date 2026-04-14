# Todo Item Card — Stage 1A Frontend

An interactive, stateful Todo Item Card extended from Stage 0. Built with semantic HTML, CSS, and vanilla JavaScript. No frameworks, no build step.

## Live URL

> https://to-do-card-nine.vercel.app/

## How to Run Locally

```bash
git clone https://github.com/Mikolo297/To-dooo.git
cd todo-card
open index.html
```

No npm install, no bundler.

---

## All Required `data-testid` Attributes

### Stage 0 (retained)

| Element               | `data-testid`                    |
|-----------------------|----------------------------------|
| Card container        | `test-todo-card`                 |
| Task title            | `test-todo-title`                |
| Task description      | `test-todo-description`          |
| Priority badge        | `test-todo-priority`             |
| Due date              | `test-todo-due-date`             |
| Time remaining        | `test-todo-time-remaining`       |
| Status indicator      | `test-todo-status`               |
| Checkbox              | `test-todo-complete-toggle`      |
| Categories list       | `test-todo-tags`                 |
| Tag (design)          | `test-todo-tag-design`           |
| Tag (mobile)          | `test-todo-tag-mobile`           |
| Tag (ux)              | `test-todo-tag-ux`               |
| Tag (q2)              | `test-todo-tag-q2`               |
| Edit button           | `test-todo-edit-button`          |
| Delete button         | `test-todo-delete-button`        |

### Stage 1A (new)

| Element                    | `data-testid`                         |
|----------------------------|---------------------------------------|
| Edit form container        | `test-todo-edit-form`                 |
| Title input                | `test-todo-edit-title-input`          |
| Description textarea       | `test-todo-edit-description-input`    |
| Priority select            | `test-todo-edit-priority-select`      |
| Due date input             | `test-todo-edit-due-date-input`       |
| Save button                | `test-todo-save-button`               |
| Cancel button              | `test-todo-cancel-button`             |
| Status dropdown            | `test-todo-status-control`            |
| Priority indicator         | `test-todo-priority-indicator`        |
| Expand/collapse toggle     | `test-todo-expand-toggle`             |
| Collapsible section        | `test-todo-collapsible-section`       |
| Overdue indicator          | `test-todo-overdue-indicator`         |

---

## What Changed from Stage 0

### Edit Mode
- Clicking Edit hides the view and shows a form (`test-todo-edit-form`) with inputs for title, description, priority, and due date.
- Save commits changes; Cancel restores the previous values from a snapshot.
- On close, focus returns to the Edit button.
- Pressing Escape also cancels edit mode.

### Status Transitions
- Status is now a `<select>` dropdown (`test-todo-status-control`) with three options: Pending, In Progress, Done.
- Changing status updates the pip indicator and status text display (`test-todo-status`) in sync.
- Setting status to Done checks the checkbox and triggers the completed visual state.
- Unchecking the checkbox reverts status to Pending.

### Priority Indicator
- A left-border strip (`test-todo-priority-indicator`) visually changes color based on priority: red (High), orange (Medium), green (Low).
- The priority badge also updates color and label when priority is changed in edit mode.

### Expand / Collapse
- Descriptions longer than 120 characters are collapsed by default (showing ~2 lines).
- A toggle button (`test-todo-expand-toggle`) reveals or hides the rest of the text.
- The toggle is keyboard accessible and updates `aria-expanded` accordingly.
- The collapsible container (`test-todo-collapsible-section`) uses `max-height` transitions.

### Time Management
- Overdue tasks show a distinct badge (`test-todo-overdue-indicator`) with `role="alert"` and `aria-live="polite"`.
- The card border also shifts to a red glow when overdue.
- When status is "Done", the time remaining display shows "Completed" and stops updating.
- Granular time labels: "Due in 45 mins", "Due in 3 hrs", "Due in 2 days", "Overdue by 1 hr".
- Updates every 30 seconds via `setInterval`.

---

## Design Decisions

- **Vanilla HTML/CSS/JS** — No framework. Single file, open in browser.
- **State object** — A plain JS `state` object holds all mutable values. All UI derives from it via `render()`, avoiding drift between elements.
- **Snapshot pattern** — Edit mode snapshots state before opening; Cancel restores it without any re-fetch.
- **CSS custom properties** — `--pri-color` drives the priority indicator; toggling a class on the card root cascades the change visually.
- **Semantic HTML** — `<form>` with `novalidate`, `<select>`, `<time datetime="">`, `<label for>`, `<ul role="list">`.

---

## Accessibility Notes

- All icon-only buttons have `aria-label`.
- Expand toggle uses `aria-expanded` and `aria-controls`.
- Overdue badge uses `role="alert"` and `aria-live="polite"` for screen reader announcement.
- Status control is a native `<select>` — fully keyboard navigable.
- Edit form uses `<label for>` on every input.
- Escape key closes edit mode.
- Focus returns to the Edit button when edit mode closes.
- Priority and status use color + text, never color alone.

---

## Known Limitations

- No persistence — state resets on page refresh.
- Tags are not editable in the form (out of scope for Stage 1A).
- Focus trap inside the edit form is not implemented (marked optional in brief).
- Due date input uses `type="date"` which inherits OS/browser styling in some environments.