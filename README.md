# $200/Day Digital Product Shop — Runbook

This is an automated AI-prompt-pack business on Gumroad. I (Claude) generate the products, listings, and marketing content on a schedule. You (Ethan) do ~15 minutes of platform work per day.

## Honest revenue math

Gumroad takes ~10% + payment fees, so a $17 pack nets ~$15.

| Daily sales | Gross | Net  |
|-------------|-------|------|
| 15 × $17    | $255  | $225 |
| 8  × $29    | $232  | $204 |
| 25 × $9     | $225  | $200 |

**Getting there is the real work.** Month 1: 0–5 sales/day while traffic warms up. Month 3–6: $200/day is plausible with 10–20 SKUs and consistent traffic from X/Threads/Reddit. Most shops plateau at $50–150/day. Some never hit $200. There are no guarantees.

## What I automate

- Product generation (new prompt packs on a weekly cadence)
- Gumroad listing copy (title, description, tags, pricing)
- Launch content (X threads, Reddit posts, LinkedIn carousels, Threads posts)
- Drip content to keep products in feed (3 posts/week per active product)
- Weekly sales review + recommendations (once you connect Gumroad data)

## What you must do (the unavoidable human parts)

**One-time (1–2 hours):**
- Create Gumroad account + connect Stripe/PayPal for payouts
- Create X, Threads, Reddit accounts if you don't have them
- Follow `ops/setup-checklist.md`

**Every day (~15 min):**
- Copy this week's generated post(s) into X/Threads/Reddit
- Upload any new products to Gumroad (takes ~3 min per product)
- Reply to any customer DMs or refund requests

**Every week (~30 min):**
- Run `/loop` to have me generate the next product + content batch
- Review sales, remove underperformers, double-down on winners

## Directory layout

```
products/        Finished prompt packs (upload these to Gumroad)
marketing/       Listing copy + social content per product
ops/             Checklists — read these first
generator/       Roadmap + templates for future products
```

## Start here

1. Read `ops/setup-checklist.md` and complete one-time setup
2. Upload `products/pack-01-claude-code-prompts/` to Gumroad
3. Post from `marketing/pack-01-launch-content.md` on launch day
4. Invoke me weekly with `/loop 7d` to continue the pipeline (or I'll schedule it for you — see below)

## Reality check

If after 90 days you're under $20/day, the niche is wrong — pivot, don't quit. If under $5/day, the products aren't good enough — I iterate on quality, not volume.
