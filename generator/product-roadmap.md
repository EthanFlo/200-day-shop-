# Product Roadmap

10 packs over ~10 weeks. Ship one per week. Each targets a distinct buyer so they don't cannibalize.

When weekly cron fires, I pick the next unbuilt pack from this list, generate the product + listing + launch content, and queue it for your approval.

---

## Shipped

- **Pack 01 — 50 Claude Code Power-User Prompts** *(flagship)*
  - Buyer: senior engineers using Claude Code
  - Price: $29 ($17 launch)
  - Status: ready to upload

## Queue (priority order)

### Pack 02 — Cursor IDE Power Pack
- Buyer: Cursor users (huge overlap with Claude Code but distinct community)
- Contents: 40 prompts specific to Cursor's agent mode, tab completion, and composer
- Price: $29
- Why priority: riding Cursor's growth wave, near-zero additional research required

### Pack 03 — AI Agent Testing Playbook
- Buyer: engineers building with Claude/GPT APIs who need eval + testing discipline
- Contents: test strategies, eval rubrics, regression harnesses, production monitoring patterns, 20 prompts
- Price: $39 (higher — clear enterprise value)
- Why: fills a real gap; buyers have budget

### Pack 04 — Prompt Engineering for B2B Sales
- Buyer: AEs and SDRs using AI for outreach
- Contents: 60 prompts for research, drafting, objection handling, follow-ups
- Price: $29
- Why: adjacent audience, high willingness-to-pay, fast to write

### Pack 05 — Claude Code for Data Engineers
- Buyer: data engineers / analytics engineers
- Contents: 40 prompts for dbt, SQL review, pipeline design, schema migrations, lineage analysis
- Price: $29
- Why: underserved niche; buyers use Claude Code less but need it more

### Pack 06 — The Incident Response Prompt Pack
- Buyer: SREs, platform engineers, oncall rotations
- Contents: 30 prompts for triage, postmortems, runbooks, comms, blame-free analysis
- Price: $39
- Why: premium audience; pain is high and immediate

### Pack 07 — Founder's AI Workflow
- Buyer: solo founders / seed-stage
- Contents: customer discovery, fundraising prep, pitch drafting, metrics analysis, legal triage
- Price: $49
- Why: highest price tolerance; broader audience than dev-focused packs

### Pack 08 — Technical Interview Prep with Claude Code
- Buyer: job-seeking senior engineers
- Contents: system design drills, leetcode debugging, behavioral prep, resume review, offer negotiation
- Price: $39
- Why: evergreen demand; buyers are motivated (income at stake)

### Pack 09 — Legacy Code Rescue Pack
- Buyer: engineers stuck in legacy codebases
- Contents: 40 prompts for reverse engineering, safe modernization, migration planning, team buy-in
- Price: $29
- Why: niche with deep pain; word-of-mouth travels well

### Pack 10 — The Ultimate Bundle
- Buyer: existing customers + big spenders
- Contents: packs 01–09 + a 20-prompt "unreleased" bonus set
- Price: $149 (vs $310 separately — but keep bundle discount at ~50%)
- Why: 1 big sale ≈ 10 small ones; drives customer LTV

---

## Non-prompt-pack expansions (consider after month 3)

Only pursue if monthly revenue is on pace for $6k+:

- **Cohort workshop** — 90-min live session, $99/seat, 20 seats, 1x/month. Teach one advanced prompt category in depth. Recording becomes Pack 11+.
- **Notion templates** — AI-assisted engineering notebooks, project trackers. Different audience, higher margin.
- **Team license of flagship** — $299 for 10-seat enterprise license. One buyer > 10 individual buyers in ops overhead.

## Don't pursue (known traps)

- **Subscription for "weekly prompt updates"** — churn is brutal, support burden high
- **Free newsletter as lead magnet** — takes 6 months before it funnels meaningfully; not worth the time sink now
- **AI-generated video content** — quality bar is crossing a cliff, by month 3 this probably won't work

---

## How I pick next week's pack

Weekly when cron fires, I:
1. Check which packs are shipped vs queued.
2. Pull Gumroad data (when connected) — if pack 01 is selling well to engineers, pack 02 (Cursor, same buyer) ships next. If flat, I pivot earlier to adjacent buyers (pack 04, pack 07).
3. Draft the next pack's prompts, listing, launch content.
4. Notify you via the output file for your approval before you upload.
