# Components

Inventory of the dashboard's UI patterns — what each is for, its states, and its rules. Code references point into `linkclipper/dashboard/dashboard.css` (class prefixes noted).

## Surfaces

### Aurora page
Fixed 4-radial-gradient backdrop on `#080b18` (see `tokens.css`). Never animates. All panels sit *on* it.

### Glass panel (`.panel`, modals, popovers)
Panel gradient + `--stroke` border + `--glow` when elevated (modal). Radius `--radius` (16px). **No `backdrop-filter` — BANNED** (Brave GPU artifacts, verified). Text contrast must hold against the *panel gradient*, not the aurora.

### Floating window (watch_popup player)
A real OS window, docked right; portrait for Shorts. It is *not* themable — don't try. Dashboard communicates it with the "Play in floating window" pill.

## Navigation

### Sidebar (`.side`)
Glass panel list; active item = `--brand-tint` fill + `--brand-line` border. Board chips show their dot in the board's `color`. Counts right-aligned in `--sub`.

### Topbar + search
Search input is a glass field; `/` focuses. Filter selects are native `<select>`s styled on glass (`background: #131735` on the dropdown list only).

## Content cards

### Item card (masonry, `.board-item`)
Cover art top (photo thumb or type-tile gradient), type pill top-left, title in `--ink`, source + time in `--sub`, tags as small chips, action chip row bottom-right (preview `--ok`, open `--inf`, delete `--bad`, move = brand gradient). Card hover lifts border to `--stroke-hi`.

### Tag chip
Small pill, `--brand-tint` fill on hover, dim border. Tags never appear without their row also showing the item's board.

### Board card (edit mode)
Name + dot + description; delete affordance only on hover (`.board-del` → `--bad`).

## Overlays

### Modal (edit item / edit board / sync)
Glass panel, `--glow`, header with title, content scrollable, footer row: destructive left (Delete, `--bad` ghost), neutral+primary right (Close, Save). **Modals never auto-save** — explicit Save with visual press feedback is part of the trust model.

### Quick-save dialog (in-page)
Compact glass, one input for note/tags, board select; same no-silent-save rule.

### Reader pane (`.reader-text`)
Article rendering inside the dashboard: max readable measure, `--ink` on plain panel (no imagery behind text), `.reader-text.warn` variant paints the extraction-failure guidance.

## Motion

- Transitions 120–160ms ease-out on hover/press only.
- No entrance animations on masonry (cards must not shift once counted/count).
- Everything usable with reduced motion; nothing depends on transform.

## Copy rules (shared with brand)

Feature-verb-noun; no exclamation marks; "floating window" always described plainly when YouTube is involved (never implying an in-dashboard embed).
