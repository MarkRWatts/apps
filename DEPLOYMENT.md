# Deployment — apps.markrwatts.com

Follows `~/claude-code/DOCKER-DEPLOY-PLAYBOOK.md` exactly, minus everything
that doesn't apply to a static site (no database, no `.env.docker`, no backup
line — there is nothing to back up).

- **Host**: `apps.markrwatts.com` → A record (DNS only) → VM LAN IP.
- **Certs**: acme-dns delegation, own registration (`APPS_ACMEDNS_*` vars in
  `~/edge/.env` **and** mirrored in the `environment:` block of
  `~/edge/docker-compose.yml` — both, or Caddy crash-loops).
- **Caddy site block**: `reverse_proxy apps:3000` (alias set in
  `docker-compose.prod.yml`).

## Update

```bash
ssh deploy@srvclaudedockerapps.lan
cd ~/apps
git pull
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d --build
```

Note: no `--env-file .env.docker` here, unlike the other apps — this app has
no env file at all.
