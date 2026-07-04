# signalfireaim.io

Signal Fire Aim — GTM intelligence and thought leadership for the agentic era.
Static single-page site, deployed via GitHub Pages (no build step, no framework).

## Structure
- `index.html` — the entire site
- `assets/brand-kit/` — source-of-truth logo, favicon, and social assets (horse-and-cart mark)
- `CNAME` — custom domain config for GitHub Pages

## Workflow
- **Content/design changes:** push to the `staging` branch and open a PR into `main`. Review the diff, then merge — this keeps a checkpoint before anything goes live rather than pushing straight to production.
- **Signal strip date:** stamped automatically by `.github/workflows/stamp-date.yml` on every push to `main`. No need to hand-type the date — the Action corrects it from the actual push date.
- **Seasonal content:** any block wrapped in `<!-- SEASONAL ... --> ... <!-- END SEASONAL ... -->` (or the CSS equivalent `/* ══ SEASONAL ... ══ */`) is auto-removed on August 1 each year by `.github/workflows/seasonal-cleanup.yml`. Wrap any time-boxed feature (holidays, launches, etc.) in these markers and it cleans itself up — update the cron schedule in that file if the expiry date isn't July 31.

## DNS / SSL
Managed through GoDaddy; SSL via GitHub Pages / Let's Encrypt.
