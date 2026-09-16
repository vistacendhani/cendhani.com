# cendhani.com

Canonical source for the public Vista Cendhani website.

Routes:
- `/` Home
- `/english/` English coaching
- `/indonesian/` Indonesian lessons

Production:
- Hosted on the existing VPS with Caddy.
- Live web root: `/srv/cendhani.com`
- Repository checkout on VPS: `/opt/cendhani.com`
- GitHub `main` is the source of truth for site code.

Deployment:
- Manual, one-command deployment from GitHub to production.
- Run: `sudo systemctl start cendhani-deploy.service`
- The service fetches `main`, resets the VPS checkout to `origin/main`, verifies the three HTML entry points, and then rsyncs the public site files to `/srv/cendhani.com`.
- The current `assets/` directory is intentionally preserved during deploys because the headshot binary is not yet stored in this repository.
- Caddy does not need to be reloaded for normal static-site content changes.

Safety rule:
- Do not edit production HTML directly except for emergency recovery.
- Commit changes to `main`, then run the deploy service.
- If a deployment fails its pre-checks, the live site should remain untouched.
