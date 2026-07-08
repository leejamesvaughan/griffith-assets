# Griffith Assets

Public CDN-hosted assets (SVG icons, images) for use in external pages where the main `griffith-app-system` repo can't be referenced directly.

## Usage via jsDelivr

```
https://cdn.jsdelivr.net/gh/leejamesvaughan/griffith-assets@main/{path}
```

Example:

```html
<img src="https://cdn.jsdelivr.net/gh/leejamesvaughan/griffith-assets@main/teicons/calendar.svg" alt="Calendar" width="48" height="48">
```

Use `@main` for the latest, or pin to a tag (e.g. `@v1.0`) for production stability.

## Folders

- `teicons/` — TimeEdit-related icons (calendar, search, eye, pin, etc.)
- `css/` — Griffith design-system stylesheets (canonical; see `griffith-app-system` LOGIC.md D8)
- `fonts/` — Griffith Sans Display (Regular + Bold), referenced by `css/theme.css`

## Design-system CSS (for React consumers)

Import in the React project's `tailwind.css`, in this order (both Griffith files are unlayered, so they beat HeroUI's `@layer`; `components-react.css` comes after `components.css` so its overrides win):

```css
@import url("https://cdn.jsdelivr.net/gh/leejamesvaughan/griffith-assets@main/css/components.css");
@import url("https://cdn.jsdelivr.net/gh/leejamesvaughan/griffith-assets@main/css/components-react.css");
@import "tailwindcss";
@import "@heroui/react/styles";
```

- **`components.css`** — canonical component styles (light-only). Plain CSS, safe to import at runtime.
- **`components-react.css`** — React/HeroUI-only overlay (collision fixes + react-aria recolours).
- **`theme.css`** — `@theme`/`@utility` tokens + `@font-face`. **Must be vendored + build-processed by Tailwind**, not runtime-imported (Tailwind can't process `@theme` from a CDN import). This hosted copy points `@font-face` at the absolute jsDelivr font URLs so it resolves wherever it's vendored.

**Updates are automatic — do not hand-edit the files in `css/`.** They are auto-published from the `griffith-app-system` repo (`scripts/publish-css.sh`, run by a post-commit hook), which pushes changes here and purges jsDelivr. Consumers use the stable `@main` URLs above (no `?v=`); refreshes arrive on their own via the purge.
