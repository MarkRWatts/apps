# apps.markrwatts.com

A static landing page for the self-hosted apps on `srvclaudedockerapps` — one
place to reach everything without remembering each hostname.

Links to:

| App | Host |
| --- | --- |
| re:Fresh | refresh.markrwatts.com |
| MediaVault | mediavault.markrwatts.com |
| Jingle Jotter | staging.jinglejotter.com |
| Job Application Tracker | jobapptracker.markrwatts.com |

Pure static HTML/CSS in `site/`, served by Caddy's `file_server` on port 3000
inside the container. No build step, no database, no env vars.

Card imagery is cropped from each app's own README screenshots
(`site/assets/`); the Job Tracker card is a hand-drawn SVG in the app's style,
since that repo has no screenshots.

## Local dev

```bash
docker compose up --build
```

Then open <http://localhost:3004>.

## Deploy

See [DEPLOYMENT.md](DEPLOYMENT.md) — standard playbook pattern
(git pull on the VM, compose up behind the shared edge Caddy).
