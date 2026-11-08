# LinkClipper design system

Product design specs — the rules and tokens the dashboard UI obeys. **Identity** assets (logo, icons, screenshots) live in [`linkclipper/brand`](https://github.com/linkclipper/brand); this repo is about *how the product looks and behaves*, so any new surface (Phase D web app, public board pages) stays consistent without copying CSS by eye.

## Layout

| Path | Contents |
|---|---|
| `tokens.css` | The canonical design tokens (mirrored from `linkclipper/dashboard/dashboard.css`) |
| `components.md` | Inventory of UI patterns with rules and states |

## Using it

- New UI: start from `tokens.css` + an existing component as a template. Don't invent a second radius scale.
- Tokens here and in the product CSS can drift — when they do, the **product CSS wins**, and this repo is updated in the same PR (or flagged in Progress-Memory if forgotten).
- The two hard laws: **no `backdrop-filter`** (Brave/Chromium GPU artifacts), **no animated aurora**. Everything glassy is translucent gradients + 1px strokes + glow.
