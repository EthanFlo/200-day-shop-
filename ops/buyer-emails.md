# Buyer Email Sequence

Three emails, sent automatically via Gumroad's Workflow feature or manually if you prefer to keep it hand-crafted. The point is to maximize buyer delight, surface cross-sells without being pushy, and build a list of repeat customers.

Configure in Gumroad: Workflows → Create new → Triggered by "product purchase" → set the delay per email.

---

## Email 1 — Post-purchase (sent immediately)

**Subject:**
```
Your 50 Claude Code prompts — a quick note
```

**Body:**
```
Hey {{name}},

Thanks for buying. The pack is attached to this email and available anytime in your Gumroad library.

Three things to know:

1. Updates are free. Any time I ship a revision (based on reader reports), Gumroad pushes it to your library. No action on your end.

2. If a prompt doesn't work for your stack, reply to this email. I fix it and push the update. Your feedback becomes the next version of the pack.

3. I'm shipping a companion pack for Cursor IDE next week. Existing buyers get 40% off — I'll email the code when it launches. You don't need to sign up for anything.

Go use #1 on your next PR review. It's the prompt I wrote first and kept coming back to.

— Ethan
```

**Tone:** warm, specific, no hype. Do not use em-dashes everywhere just because AI loves them — sprinkle sparingly.

---

## Email 2 — Day 7 (if they haven't opened the file)

**Subject:**
```
You haven't opened the prompts yet — that's OK, but here's the one I'd start with
```

**Body:**
```
Hey {{name}},

Noticed you haven't pulled the file down yet — life happens. If it's the kind of thing where you'll forget it exists unless I nudge, consider this the nudge.

If you only try one prompt this week, make it this:

"Review the diff on my current branch against main as if you were a staff engineer. Flag: (1) logic bugs, (2) missed edge cases, (3) security issues, (4) perf regressions, (5) anything that disagrees with existing patterns. Output in severity order with file:line and suggested fix."

Catches ~1 real issue in 3 PRs for me. Ten seconds to paste. Worth it.

If it ends up not useful, reply with "refund" — I'll process it, no questions. Don't let it sit there feeling guilty.

— Ethan
```

**When to trigger:** Day 7 after purchase, ONLY if Gumroad tracks they haven't downloaded the file. If you can't detect that, skip this email rather than spam everyone.

---

## Email 3 — Day 30 (quiet cross-sell)

**Subject:**
```
What's working (and what you asked for)
```

**Body:**
```
Hey {{name}},

30 days since you grabbed the prompt pack. A few updates:

New prompts added this month (free in your library):
- #51: Database migration safety check
- #52: "This test is flaky" deep triage
- #53: Security-review a third-party library before adopting

New pack shipped: Cursor IDE Power-User Prompts (40 prompts, labeled by mode). As a pack-01 buyer, you get 40% off with code `COMEBACK40`:
{{pack-02 link}}

And something I wanted to ask: what's the next pack you'd buy? Reply with one line. Top 3 answers become the next 3 packs. Everyone who replies gets the resulting pack for free.

— Ethan
```

**Notes:**
- Only send if you've actually added new prompts. Don't lie.
- The ask at the end is the single highest-leverage move of the entire funnel. Replies become your customer-driven roadmap + a repeat-customer list.

---

## Setup in Gumroad

1. Gumroad dashboard → **Workflows** → **New workflow**
2. Trigger: "When a sale happens for product [pack-01]"
3. Add email 1 — delay: 0 minutes. Paste subject + body. Variables `{{name}}` render from buyer data.
4. Add email 2 — delay: 7 days.
5. Add email 3 — delay: 30 days.
6. Turn workflow ON.

## Measurement

Open rate > 40%: subject lines are working. Reply rate > 5% to email 3: you're building a real list. Refund rate after email 2: should be ≤1%. If email 2 triggers refunds, the pack isn't matching buyer expectations — fix the listing, not the email.

## Sequence updates

These emails evolve. If you learn something from reader replies (email 3), revise email 1 to reference it. Tighten. Don't let emails rot.
