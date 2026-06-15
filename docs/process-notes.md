# Process Notes

Append-only per-session log.

## 2026-06-15 — Renamed nsrt → website; cleanup + handbook link
- **Done:** Renamed the repo nsrt → `NSRelaTech/website` (GitHub + local; GitHub redirects preserved). Moved the Feb meetup materials out to `NSRelaTech/meetups`. Updated the Telegram invite link (5 footer/CTA/empty-state links → `t.me/+lSxJDH1fLHczNjU0`). Added a trilingual "Citizen's Handbook" card to "Our First MVPs" (→ novi-sad-handbook.netlify.app). Deployed all to nsrt.netlify.app. Repo later moved under the local `NSRelaTech/` umbrella folder.
- **Decisions:** Live URL stays `nsrt.netlify.app` (only the repo name changed). Handbook featured as an MVP card, not a footer link (Artem's call).
- **State:** Live; website-only (landing page + OG assets). Clean + pushed.
- **Next:** none.
- **Deploy gotcha:** ALWAYS deploy from the website dir with `--site=7ab9511e-c16b-404f-baa4-3e24ef0259f6` — the workspace shell cwd (a Next.js app) misleads the Netlify CLI. See `claude-config/memory/reference_netlify_deploy_cwd_site.md`.
