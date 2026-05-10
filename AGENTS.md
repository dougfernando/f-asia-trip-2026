# Repository Guidelines

## Project Structure & Module Organization

This repository contains a static trip companion app.

- `app.html` is the primary application file. It includes markup, inline CSS, JavaScript, PWA metadata, and the editable `CONFIG` object for itinerary, companies, city guides, flights, hotels, and labels.
- `sw.js` is the service worker/offline companion file. Keep its cached routes and app content aligned with `app.html` when changing offline behavior.
- There is no package manifest, source directory, asset folder, or dedicated test directory. Embedded data URIs provide app icons and manifest content.

## Build, Test, and Development Commands

No build step is required. Open the app directly in a browser:

```sh
open app.html
```

For local testing with service-worker behavior, serve the directory over HTTP:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000/app.html`. Use DevTools to inspect console errors, responsive layout, cache storage, and service-worker registration.

## Coding Style & Naming Conventions

Use two-space indentation for HTML, CSS, and JavaScript. Keep user-facing trip content inside the `CONFIG` object where possible.

Use descriptive keys that match nearby data, for example `morning_summary`, `themeButtonText`, or `searchPlaceholder`. Preserve ISO dates (`YYYY-MM-DD`) for itinerary and transport data.

## Testing Guidelines

There is no automated test framework yet. Before committing, manually verify:

- `app.html` loads without console errors.
- Search and tab navigation work for Itinerary, Companies, Cities, and Logistics.
- Mobile and desktop layouts remain readable.
- Offline/PWA behavior still works after refreshing through the local HTTP server.

If automated tests are added later, document the command here and place tests in `tests/` or beside the code they validate.

## Commit & Pull Request Guidelines

The current history uses a concise style such as `Initial commit: Asia Trip 2026 companion app`. Continue using commit subjects that name the affected area, for example `Update Singapore logistics` or `Fix offline cache version`.

Pull requests should include a short description, affected trip dates or sections, manual verification steps, and screenshots for visible UI changes. Link source documents when updating itinerary, flight, hotel, or meeting details.

## Agent-Specific Instructions

Keep edits focused. Do not introduce build tooling, dependencies, or file splits unless requested or clearly needed. Treat itinerary and logistics data as high-impact content: verify dates, times, names, and addresses before changing them.
