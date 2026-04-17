# Pack-02 Launch Content

Replace `[LINK]` with your Gumroad product URL + UTM (same conventions as pack-01).

---

## X / Twitter — Launch thread

**Tweet 1**
```
Most "Cursor prompt packs" are just "Claude Code prompts" with the word Cursor swapped in.

This one isn't. Every prompt is labeled for the mode it works in — Composer, Chat, Inline. Because a Composer prompt and a Chat prompt shouldn't read the same.

5 favorites ↓
```

**Tweet 2**
```
1/ [Composer] The refactor prompt that stops Composer from touching 40 files when it only needed to touch 6:

"Refactor {concept} across the repo. Before touching anything, list every file you plan to modify and a one-line reason per file. Wait for me to confirm. Only then apply changes."
```

**Tweet 3**
```
2/ [Chat] The "will this break anything" check:

"If I change {function} to {new behavior}, what breaks? Trace every caller including tests and fixtures. List each with the specific assumption that would fail."

Beats "looks fine to me."
```

**Tweet 4**
```
3/ [Inline] Cmd-K prompt I use 10x/day — tighten without changing behavior:

"Refactor this function for clarity. Same inputs → same outputs → no new branches. Favor early returns over nested ifs. Preserve comments that explain WHY. Drop comments that just restate code."
```

**Tweet 5**
```
4/ [.cursorrules] Conservative-refactor rule that prevents Cursor from "helpfully" renaming unrelated stuff:

"When asked to refactor, default to smallest possible change. Do not rename unrelated symbols, reformat files not in the ask, introduce abstractions speculatively, or update dependencies."
```

**Tweet 6**
```
5/ [Chat] Broken Composer session recovery:

"Composer made changes across {N} files and {tests/build} is red. Diagnose: read the diff, identify which change broke what, propose the minimal revert. Don't revert everything — isolate the bad change."

Saves you from panic-undoing.
```

**Tweet 7**
```
The other 35 are in the pack — Composer multi-file changes, Chat archaeology, Inline edits, .cursorrules that stop Cursor from being too helpful, and 5 session-flow prompts for starting/ending work cleanly.

$17 launch (code LAUNCH17), $29 after. Single markdown file. [LINK]
```

**Tweet 8 (optional cross-sell to pack-01)**
```
If you use Claude Code too: the 50 Claude Code Power-User Prompts pack pairs with this one. Separate tool, separate prompts. Bundle discount coming soon. [pack-01 LINK]
```

---

## Reddit — r/cursor, r/ChatGPTPromptGenius

**Title**
```
I wrote 40 Cursor prompts organized by mode — Composer vs Chat vs Inline. Sharing 5 I use every day
```

**Body**
```
Most Cursor prompt packs treat every prompt the same. But a Composer prompt (agent, multi-file) and an Inline Cmd-K prompt shouldn't read the same way — different context, different expected output, different failure modes. I spent a while building 40 prompts each labeled for their mode. Sharing the 5 I use most.

**1. [Composer] Multi-file refactor with explicit touch list**
> Refactor {concept} across the repo. Before touching anything, list every file you plan to modify and a one-line reason per file. Wait for me to confirm or trim the list. Only then apply changes.

Stops Composer from touching 40 files when it needed 6.

**2. [Chat] "What breaks if I change this?"**
> If I change {function} to {new behavior}, what breaks? Trace every caller including tests and fixtures. List each with the specific assumption that would fail.

Pre-flight check before a risky change.

**3. [Inline] Tighten without changing behavior**
> Refactor this function for clarity. Same inputs → same outputs → no new branches. Favor early returns. Preserve WHY comments, drop comments that just restate code.

Cmd-K this, 10x a day.

**4. [.cursorrules] Conservative-refactor rule**
> When asked to refactor, default to smallest possible change. Do not rename unrelated symbols, reformat files not in the ask, introduce abstractions speculatively, or update dependencies.

Stops Cursor from being too helpful.

**5. [Chat] Broken Composer session recovery**
> Composer made changes across {N} files and {tests/build} is red. Diagnose: read the diff, identify which change broke what, propose the minimal revert. Don't revert everything — isolate the bad change.

Saves you from panic-undoing.

The other 35 cover Composer agent-mode refactors, Chat archaeology, Inline one-liners, .cursorrules for TS/Python/refactor-discipline, and 5 session-flow prompts. Full pack: [LINK] — $17 through Friday, $29 after.

Happy to answer structure questions.
```

---

## LinkedIn

**Hook**
```
Every "Cursor prompt pack" I've seen treats Composer prompts and Inline Cmd-K prompts identically. They shouldn't be. Different modes need different prompt shapes.

Spent a while building 40 prompts each labeled for the mode they're designed for. Sharing 5 I use daily:
```

**Body**
```
1️⃣ [Composer] Multi-file refactor — force a touch-list approval before edits
2️⃣ [Chat] "What breaks if I change this?" — trace callers before committing
3️⃣ [Inline] Tighten-this-function — same behavior, cleaner code
4️⃣ [.cursorrules] Conservative refactor — stop Cursor from renaming unrelated code
5️⃣ [Chat] Broken Composer recovery — isolate which change broke the build

The pack covers 5 sections: Composer, Chat, Inline, .cursorrules, and session flow.

Link in comments. $17 launch price through Friday.

— Ethan
```

**First comment**
```
[LINK]
```

---

## Threads

**Post 1**
```
Shipped: 40 Cursor prompts labeled by mode — Composer vs Chat vs Inline vs .cursorrules. Every prompt is designed for where you'll actually use it. $17 launch → [LINK]
```

**Post 2**
```
The [.cursorrules] I put in every repo now:

"When asked to refactor, default to smallest possible change. Do not rename unrelated symbols, reformat files not in the ask, introduce abstractions speculatively, or update dependencies."

Cursor being "helpful" is what I'm protecting myself from.
```

**Post 3**
```
[Composer] prompt that's saved me hours:

"List every file you plan to modify and a one-line reason per file. Wait for me to confirm. Only then apply changes."

Composer will happily touch 40 files when 6 was right. This forces the plan first.
```

**Post 4**
```
The pack: 10 Composer, 10 Chat, 10 Inline, 5 .cursorrules, 5 session flow. One markdown file. [LINK]
```

---

## Drip schedule
Daily trigger will generate ongoing content starting next Tue. Until then, post these in order: X thread day 1, Reddit day 1 (90 min after X), LinkedIn day 1 (afternoon, link in comments), Threads across days 1–3.
