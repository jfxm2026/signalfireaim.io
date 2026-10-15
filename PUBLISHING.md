# Publishing playbook (approval-gated)

The rule: **Claude researches → James reviews one email → James replies APPROVE → Claude publishes.**
Nothing goes live on either site without an APPROVE reply from james@signalfireaim.io.

## The daily loop
1. **5:47 AM ET — IAM briefing** (research only). Saves `IAM Daily Briefing — <date>` to Drive. Never pushes.
2. **6:12 AM ET — Daily brief email** `APPROVE: Daily brief - <date>`. Ends with a `WEBSITE UPDATES` block
   (between `=== WEBSITE UPDATES ===` and `=== END WEBSITE UPDATES ===`) listing exact changes for both sites.
3. **Mondays 6:59 AM ET — Global AI Watch refresh**. Saves the full proposed `global-ai-watch.html` to Drive and
   emails `APPROVE: Global AI Watch - <date>` with the Drive link. Never pushes.
4. **Hourly 7 AM–9 PM ET — Publisher** checks Gmail for James's replies on `APPROVE:` threads from the last 3 days.
   - Reply contains "approve" (any case) → apply that thread's WEBSITE UPDATES (plus any edits in the reply), push to the `staging` branch
     of signalfireaim.io (`publish-approved.yml` then takes `staging` live on `main`), then reply on the thread `PUBLISHED: <what changed>` with the live links.
   - Reply has edits but no "approve" → revise, reply on the thread with the revised block, wait for APPROVE.
   - Already answered with `PUBLISHED:` or `REVISED:` after James's latest reply → skip (never publish twice).

## What can change, and where
| Item | Repo / file | How |
|---|---|---|
| Red BREAKING banner | signalfireaim.io `alert.json` | `{"active": true, "text", "link", "updated"}`; set `"active": false` once older than ~3 days |
| Signal strip / article rows | signalfireaim.io `index.html` | Edit only the named strip items or rows. The date stamps itself on push. |
| Global AI Watch | signalfireaim.io `global-ai-watch.html` | Apply the approved row/price/Solo.io edits, or the full approved file from Drive |
| LTG "Latest signal" | signalfireaim.io `latest.json` (lucastaylorgroup.com reads it from https://signalfireaim.io/latest.json) | `{"active": true, "text": "<one line>", "link": "<signalfireaim.io url>", "date": "<Mon D, YYYY>"}` |

## Standing rules (check every publish)
- Email is the only contact method. Never publish a phone number.
- LucasTaylor Consulting Group (LTG) started in **2011**.
- No links to redirects; use the final URL readers will land on.
- Public pages carry no internal commentary, plans or critiques.
- Never name or tag a vendor or person as if they endorse James.

## LTG site
lucastaylorgroup.com is served from jfxm3671/LTG.github.io (not the jfxm2026 fork). Daily updates never touch it: its Latest signal line reads signalfireaim.io/latest.json. Page redesigns go through a pull request from jfxm2026:publish-ltg that James merges.
