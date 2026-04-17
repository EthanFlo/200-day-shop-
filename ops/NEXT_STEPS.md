# Next Steps

## Automation status

**Repo:** https://github.com/EthanFlo/200-day-shop-

**Trigger 1 — Weekly product pipeline**
- ID: `trig_01DxkHsnEsEUJHni8Eg3PePw`
- Dashboard: https://claude.ai/code/scheduled/trig_01DxkHsnEsEUJHni8Eg3PePw
- Runs: every Monday at 8:00 AM PDT (15:00 UTC). First run: **Monday 2026-04-20**.
- What it does: ships next pack from roadmap (product + listing + launch content), generates drip for shipped packs, updates roadmap, writes weekly brief, commits + pushes.

**Trigger 2 — Daily social digest**
- ID: `trig_01Xay9csDfDZBaBqRZkx6Cm6`
- Dashboard: https://claude.ai/code/scheduled/trig_01Xay9csDfDZBaBqRZkx6Cm6
- Runs: Tue–Fri at 7:00 AM PDT (14:00 UTC). First run: **Tuesday 2026-04-21**.
- What it does: drafts that day's X/Threads/LinkedIn/Reddit posts for shipped packs; commits to `ops/daily-digests/YYYY-MM-DD.md`. You open that file each morning, copy posts, queue in your scheduler.

After each run, `git pull` to get the output.

## 🚨 Required: 2-click GitHub auth fix

The triggers failed first-run authorization (expected — fresh repo). Fix:

1. Go to: **https://github.com/apps/claude** (or https://github.com/settings/installations if already installed)
2. Install (or configure) → select **Only select repositories** → pick `EthanFlo/200-day-shop-` → grant **read + write**.
3. Done. Both triggers will work on their next scheduled fire.

To test before waiting, hit "Run now" on either dashboard link above.

## This week (before first Monday run)

**Priority: launch pack-01 so the pipeline has a live product to drip-market while pack-02 builds.**

1. Complete `ops/setup-checklist.md` (Gumroad account, social accounts, payouts). ~1–2 hours. One-time.
2. Upload `products/pack-01-claude-code-prompts/` to Gumroad using copy from `marketing/pack-01-gumroad-listing.md`. ~15 min.
3. On launch day (pick Tue or Wed), post launch content from `marketing/pack-01-launch-content.md` across X, Reddit, LinkedIn, Threads. ~30 min.

## Weekly rhythm (after first Monday run)

Monday: `git pull`, read `ops/weekly-briefs/{YYYY-WW}.md`, upload the week's new pack, queue the week's posts in your scheduler.
Tue–Fri: ~5 min/day replying to comments and DMs.
Sat: check Gumroad dashboard, jot numbers into `ops/status.md`.
Sun: off.

## If the first Monday run fails

Most common failure: the remote agent doesn't have permission to push back to your private repo. Symptom: you'll see no new commits Monday morning.

Fix:
1. Go to https://github.com/settings/installations
2. Confirm Claude / Anthropic GitHub App has access to `EthanFlo/200-day-shop-` with write permissions.
3. If not installed: install it, grant access to this repo.
4. Next Monday's run will work.

You can also manually trigger a test run from the dashboard to verify before waiting a week.

## Cost

Each weekly run uses Sonnet and costs Anthropic compute — billed against your account. Expected: ~$1–3/run depending on how much drip content accumulates. At $200/day target, trivially worth it.

## Killing it

If you want to stop the schedule:
- Disable: dashboard link above → Disable toggle
- Delete: https://claude.ai/code/scheduled (Anthropic doesn't expose delete via API yet)
