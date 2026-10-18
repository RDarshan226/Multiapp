# Multiapp

A GitHub Pages repository designed to host multiple independent progressive web apps (PWAs) under one project.

## Current structure

- `index.html` — Multiapp hub / launcher.
- `apps/swp-goal/` — Mutual fund future-goal and SWP estimator.
- `apps/_template/` — Copyable starter for future independent PWAs.

## Publish with GitHub Pages

1. Open **Settings → Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select branch `main` and folder `/(root)`, then save.
4. Wait for the Pages deployment to finish.

Hub URL: https://RDarshan226.github.io/Multiapp/

App URL: https://RDarshan226.github.io/Multiapp/apps/swp-goal/

## Add another independent PWA

1. Copy `apps/_template/` to a new folder, for example `apps/meal-planner/`.
2. Edit that folder's `index.html`, `manifest.json`, and `sw.js`.
3. In its manifest, keep `start_url` and `scope` relative to the app folder (for example `./index.html` and `./`).
4. Give its service worker a **unique cache name**. Do not reuse another app's cache name.
5. Register its worker with a relative path: `navigator.serviceWorker.register('./sw.js')`.
6. Add a new link card to the root `index.html`.
7. Commit and push. It will be hosted at `https://RDarshan226.github.io/Multiapp/apps/meal-planner/`.

Each PWA should keep its own manifest, worker, cache namespace, and app data. A worker registered at a subdirectory scope can control only that subdirectory. Avoid registering a root-scoped worker unless you deliberately want it to control the whole hub.

## MF Future Goal Planner

The calculator estimates:
- future item cost using an inflation assumption;
- goal-date corpus from existing investment and monthly SIP;
- estimated monthly SIP required to meet the goal;
- corpus gap/surplus; and
- a simplified equal monthly SWP over a selected withdrawal period.

All calculations run locally in the browser. Returns are assumptions, not forecasts or guarantees. The calculator is educational and does not recommend a specific mutual fund or scheme.

## Notes

- GitHub Pages hosting must be enabled in repository settings before the URLs become live.
- For custom icons, add app-specific image files and reference them from that app's manifest.
- Separate PWA folders do not automatically share data. Cross-app synchronization requires a deliberately designed common data source and appropriate authentication.
