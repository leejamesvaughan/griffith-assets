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
