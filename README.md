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
- Production sync is designed to pull `main` and copy only public site files into the live web root.

Deployment rule:
- GitHub `main` is the source of truth.
- Do not edit production HTML directly except for emergency fixes.
- After a change is committed to `main`, run the sync service for an immediate deploy or let the timer deploy it automatically.
