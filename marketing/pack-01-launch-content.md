# Pack-01 Launch Content

Post order: Reddit → X thread → LinkedIn → Threads. Reddit first because it drives the longest-tail traffic and takes the most runway to gain traction.

Replace `[LINK]` with your Gumroad product URL + UTM:
- X: `?utm_source=x&utm_medium=social`
- Reddit: `?utm_source=reddit&utm_medium=social&utm_campaign=launch`
- LinkedIn: `?utm_source=linkedin&utm_medium=social`
- Threads: `?utm_source=threads&utm_medium=social`

---

## X / Twitter — Launch thread (post at 9–11am ET on a Tuesday or Wednesday)

**Tweet 1 (hook)**
```
I spent 6 months writing and rewriting prompts for Claude Code in my own work.

Shipped the 50 that actually held up across real codebases — debugging, refactors, security reviews, the whole loop.

Posting the best 5 in this thread ↓
```

**Tweet 2**
```
1/ The one I use most — PR self-review before asking a teammate:

"Review the diff on my current branch against main as if you were a staff engineer. Flag logic bugs, missed edge cases, security issues, perf regressions. Output in severity order with file:line."

Catches ~1 real bug in 3.
```

**Tweet 3**
```
2/ Stack trace triage. Someone pages you, you have 30 seconds:

"Stack trace: {paste}. Tell me the failing invariant in one sentence, the 3 most likely root causes ranked by likelihood, and the single log line that would disambiguate them."

Beats 'it's null somewhere' 100% of the time.
```

**Tweet 4**
```
3/ Dead code, with proof:

"Prove or disprove that {symbol} is dead. Check direct callers, dynamic dispatch, reflection, string-based imports, config references, and exported API surface. Conclude: safe to delete / not safe + reason."

No more "I think this is unused."
```

**Tweet 5**
```
4/ The "works on my machine" diagnosis:

"Local passes. CI fails with {error}. List every plausible environmental difference (OS, versions, env vars, case sensitivity, timezone). For each, give a one-line check to confirm or rule out."

Saves you an hour of flailing.
```

**Tweet 6**
```
5/ Rename that doesn't break prod:

"Rename {old} → {new}. Search code, docs, config, fixtures, test names, CI scripts — not just code. Produce a plan, then execute. Skip occurrences that are different symbols with the same name."

You'd be surprised what a grep-and-replace misses.
```

**Tweet 7 (the pitch)**
```
The other 45 are in the pack.

10 categories: review, debug, refactor, test, architecture, perf, security, docs, git, onboarding.

$17 launch price (code LAUNCH17), $29 after Friday. Single markdown file, works anywhere.

[LINK]
```

**Tweet 8 (social proof / credibility builder — only post if true)**
```
If you're a staff+ eng who uses Claude Code daily, send me feedback — I ship updates based on what people actually report back. Free upgrades for anyone who bought.
```

---

## Reddit — r/ChatGPTPromptGenius, r/ClaudeAI, r/ArtificialInteligence

**Subreddit rules check first:** each sub has different policies on selling. Read the sidebar before posting. If promotion isn't allowed, post the value-first version without the link and let the pack sell itself via DMs / bio.

**Title**
```
I wrote 50 Claude Code prompts for senior engineers over 6 months — here are the 5 I use most
```

**Body**
```
I've been using Claude Code daily for a while and kept rewriting the same prompts. Over 6 months I distilled them into 50 that hold up across different codebases and languages. Sharing the 5 I reach for most. Full pack linked at the bottom — ignore it if you just want the prompts.

**1. PR self-review before teammate review**
> Review the diff on my current branch against main as if you were a staff engineer. Flag: (1) logic bugs, (2) missed edge cases, (3) security issues, (4) perf regressions, (5) anything that disagrees with existing patterns in the repo. Output in severity order with file:line and suggested fix.

This catches ~1 real issue in 3 PRs for me.

**2. Stack trace triage**
> Stack trace: {paste}. Tell me: (1) the failing invariant in one sentence, (2) the 3 most likely root causes ranked by likelihood, (3) what single log line or metric would disambiguate them.

Use during an incident when you need direction fast.

**3. Dead code with proof**
> Prove or disprove that {symbol} is dead. Check direct callers, dynamic dispatch, reflection, string-based imports, config references, exported API surface, and test fixtures. Conclude: safe to delete / not safe + reason.

No more "I *think* this is unused."

**4. "Works on my machine" diagnosis**
> Local: {command} passes. CI: same command fails with {error}. List every plausible environmental difference (OS, versions, env vars, case sensitivity, timezone, locale). For each, give a one-line check I can run to confirm or rule out.

Faster than guessing.

**5. Rename across a polyglot repo**
> Rename {old} → {new}. Search the entire repo including docs, config, fixtures, test names, commit hooks, and CI scripts. Produce a plan with every file/line to change, then execute. Skip occurrences that are different symbols with the same name.

The other 45 cover refactoring, testing, architecture, perf, security, documentation, git workflows, and onboarding. If you want them, they're here: [LINK] — $17 launch price through Friday.

Happy to answer questions about how I structured them or what I found didn't work.
```

---

## LinkedIn — carousel or text post

**Hook (first 3 lines before "see more")**
```
Six months of daily Claude Code use produced 50 prompts that actually hold up across real codebases.

Most "AI prompt packs" are generic. This one isn't — every prompt is designed to let Claude use its tools (Read, Grep, Bash) to gather real context about your codebase before responding.

Sharing the 5 I reach for most:
```

**Body**
```
1️⃣ PR self-review before teammate review
Review the diff on my branch vs main as a staff engineer. Flag logic bugs, edge cases, security, perf, and pattern violations in severity order with file:line.

2️⃣ Stack trace triage
Tell me the failing invariant in one sentence, the 3 most likely root causes, and the log line that would disambiguate them.

3️⃣ Dead code with proof
Prove or disprove a symbol is dead code. Check every reference path before deletion.

4️⃣ "Works on my machine" diagnosis
List every plausible environmental difference between local and CI with a one-line check for each.

5️⃣ Polyglot-repo rename
Search code, docs, config, fixtures, test names, CI scripts — produce a plan, then execute.

The full pack covers review, debug, refactor, test, architecture, perf, security, docs, git, and onboarding.

Link in comments. $17 launch price through Friday.

— Ethan
```

**First comment (drop link here to avoid LinkedIn reach penalty)**
```
[LINK]
```

---

## Threads — short-form, 5 posts across 2 days

**Post 1 (launch day)**
```
Shipped today: 50 Claude Code prompts I've refined over 6 months of daily use. If you use Claude Code and keep rewriting the same prompts, this is built for you. $17 launch → [LINK]
```

**Post 2 (launch day +2h)**
```
Most used prompt from the pack — stack trace triage:

"Tell me the failing invariant in one sentence, the 3 most likely root causes ranked by likelihood, and the single log line that would disambiguate them."

Use during an incident. Beats staring at the trace.
```

**Post 3 (day 2)**
```
A prompt I use every PR:

"Review the diff on my branch vs main as if you were a staff engineer. Flag logic bugs, edge cases, security, perf regressions in severity order with file:line."

Catches ~1 real issue per 3 PRs.
```

**Post 4 (day 2)**
```
The pack is 10 categories: review, debug, refactor, test, architecture, perf, security, docs, git, onboarding. 5 prompts each. All copy-paste ready. [LINK]
```

**Post 5 (day 3 — only if launch traction is there)**
```
Launch price ends tomorrow — $17 instead of $29. Single markdown file, works anywhere. [LINK]
```

---

## Follow-up drip (week 2+)

After launch week, I (Claude) will generate 3 posts/week per active product to keep it in feed. These will live in `marketing/drip/pack-01/`. Don't post all at once — schedule via Typefully.
