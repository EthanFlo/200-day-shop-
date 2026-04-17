# 40 Cursor IDE Power-User Prompts

For engineers who live in Cursor's Composer, Chat, and Tab. Every prompt is mode-aware — labeled for where it works best.

**Legend**
- **[Composer]** — agent-mode, multi-file edits
- **[Chat]** — single-turn Q&A, right-side panel
- **[Inline]** — CMD-K / Tab edits in the file
- **[Any]** — works anywhere

---

## 1. Composer / Agent-Mode (10)

### #1 — Multi-file refactor with explicit touch list [Composer]
```
Refactor {concept, e.g., "auth middleware"} across the repo. Before touching
anything, list every file you plan to modify and a one-line reason per file.
Wait for me to confirm or trim the list. Only then apply changes. Do not
touch tests in the same pass.
```

### #2 — Scaffold a feature with tests next to code [Composer]
```
Create a new feature {name} following this repo's existing conventions:
read {path to a similar feature} to infer the structure. Co-locate the test
file. Do not add a new library. If an existing helper fits, use it — show me
which one and why.
```

### #3 — Apply a pattern from one module to another [Composer]
```
{Module A} uses {pattern — e.g., Result<T,E>, dependency injection}.
{Module B} doesn't. Apply the pattern to B without changing B's public
behavior. Show diffs module-by-module. Stop after each module for review.
```

### #4 — Upgrade a library with breaking changes [Composer]
```
Upgrade {library} from {old} to {new}. WebFetch the release notes first.
List every breaking change. For each, grep the repo and map usages to
"safe / needs-migration / broken". Apply the safe changes immediately;
show me the plan for the rest before touching them.
```

### #5 — Turn a script into a proper module [Composer]
```
{file} is a one-off script. Promote it to a reusable module: extract config,
separate IO from logic, add a minimal test for the core function, and export
a clean interface. Preserve the script's CLI entry point for backward
compatibility.
```

### #6 — Decompose a monolithic component [Composer]
```
{Component} in {file} is {N} lines. Split it into sub-components along the
seams of its responsibilities. Do not introduce a new state library. Keep
the public prop API of the outer component unchanged. Show the new file
tree before writing anything.
```

### #7 — Add a missing layer (e.g., service, repository) [Composer]
```
Right now the {controller/handler} talks directly to {DB/API}. Introduce a
{service/repository} layer that owns that logic. Update callers. Don't
abstract for hypothetical future needs — only what's actually called today.
```

### #8 — Migrate between state libraries [Composer]
```
Migrate {feature} from {old: e.g., Redux} to {new: e.g., Zustand}. Do one
feature at a time; don't refactor unrelated ones. Map each action/reducer
to the new API one-for-one. After the migration, the feature's behavior
should be byte-identical to before.
```

### #9 — Generate a CRUD surface from a schema [Composer]
```
Read {schema file, e.g., schema.prisma or a Pydantic model}. Generate the
CRUD API (routes, handlers, validators, tests) following the pattern of
{existing reference: path to similar CRUD}. Do not generate admin-only
endpoints unless the schema explicitly marks fields as admin.
```

### #10 — Retire a deprecated pattern across the repo [Composer]
```
{Pattern} is deprecated in our repo. Find every usage, replace with
{replacement}, and remove the old helper if it has no callers after the
pass. Run the test suite after each logical chunk — if anything goes red,
stop and surface.
```

---

## 2. Chat (right-side panel) (10)

### #11 — Ask for the WHY, not the WHAT [Chat]
```
Why is {file:lines} structured this way? Check git blame for the commit
that introduced it. If the commit message or PR explains the rationale,
summarize; if not, infer from the surrounding code and mark your inference
as a guess.
```

### #12 — "What will break if I change this?" [Chat]
```
If I change {function/type} to {new behavior}, what breaks? Trace every
caller (including tests and fixtures). List each with the specific
assumption that would fail.
```

### #13 — Tradeoffs between two in-code options [Chat]
```
I can solve {problem} with approach A ({describe or cite file}) or approach
B. Compare, grounded in this repo: maintainability given existing patterns,
performance under our actual load profile (check the monitoring config if
present), and upgrade cost. Pick one; defend the pick.
```

### #14 — Explain a dependency's API quickly [Chat]
```
I need to use {library's specific feature}. WebFetch the docs. Give me
the 5-line minimum example for our use case: {describe use case}. Skip
install and boilerplate — we already have the dep.
```

### #15 — "Is there already a helper for this?" [Chat]
```
I need to {do X}. Before I write a helper, grep the repo for existing
utilities that could fit. Rank: exact match, close match (minor adjustment),
none. If none, show me the 3 cleanest places to put a new helper.
```

### #16 — Diagnose an error without running anything [Chat]
```
Error: {paste}. Just from the message + stack + the relevant code
(identify which file), tell me: most likely root cause, the one line to
read to confirm, and the one-line fix. If the info is insufficient, say
what you'd need.
```

### #17 — Grade a PR before you hit submit [Chat]
```
Look at my uncommitted changes. Grade the PR from a staff engineer's lens:
(A) logic correctness, (B) test adequacy, (C) fit with repo conventions,
(D) readability. Letter grade each + one specific fix per weak category.
```

### #18 — "What test would catch this?" [Chat]
```
I just fixed {bug: describe}. What test would have caught it? Write the
test — prefer the highest layer that still pins the behavior (don't write
a unit test if an integration test covers it better).
```

### #19 — Context-aware rename proposal [Chat]
```
{Name} is a bad name because {reason / just ask what's better}. Propose 5
alternatives consistent with naming conventions actually used in this repo
(look at similar concepts). Rank by fit. I'll pick.
```

### #20 — "Summarize this PR/diff for a non-engineer" [Chat]
```
Summarize the current diff for a PM stakeholder in 3 bullets. No jargon.
Focus on user-visible impact, not implementation. Flag anything they need
to make a call on.
```

---

## 3. Inline (CMD-K / Tab) (10)

### #21 — Tighten a function without changing behavior [Inline]
```
Refactor this function for clarity. Same inputs → same outputs → no new
branches. Favor early returns over nested ifs. Preserve all comments that
explain WHY. Drop comments that just restate the code.
```

### #22 — Add types that weren't there [Inline]
```
Add strict types to this function. If an input can legitimately be multiple
types, use a union — don't widen to any/unknown. Do not refactor logic.
```

### #23 — Extract a helper that callers can reuse [Inline]
```
Extract the {described block} as a helper. Place it {at top of file /
in {module} — whichever is idiomatic for this repo}. Update this function
to call it. Don't over-abstract — the helper should be called from at
least 2 places or it stays inline.
```

### #24 — Write a docstring that's actually useful [Inline]
```
Write a docstring for this function. Include: what it does in one line,
each parameter's semantics (not its type — that's obvious), the failure
modes, and one example. Skip restating the obvious.
```

### #25 — Convert callback to async/await [Inline]
```
Rewrite this callback-style code as async/await. Preserve error propagation
semantics exactly — if the original swallowed an error, keep swallowing it
(but note it with a comment). Don't "improve" the error handling silently.
```

### #26 — Add input validation without a library [Inline]
```
Validate the inputs to this function. Use plain guards, no validation
library. Check for: nullish, wrong type, out-of-range values. Throw with
specific messages. Don't catch — let callers handle.
```

### #27 — Add logging that helps debugging, not noise [Inline]
```
Add logs to this function. One log at entry with inputs (redact any field
named like password/token/secret). One log per branch decision. One log at
exit with outcome. Use the repo's existing logger. No console.log.
```

### #28 — Rename a variable everywhere in file [Inline]
```
Rename {old} to {new} within this file only. Don't rename anything that
happens to share the name but is a different symbol. If you're not sure
about a reference, leave it and flag it.
```

### #29 — Wrap this in a try/catch with proper error handling [Inline]
```
Wrap this in try/catch. The catch should (a) log with context, (b) either
rethrow as a domain-specific error or return a sensible fallback —
decide which based on what the caller can do. If you rethrow, preserve
the original as `cause`.
```

### #30 — Inline a one-line helper that's called once [Inline]
```
Inline {helper} here since it's only called from this file. Delete the
helper definition. Preserve behavior exactly.
```

---

## 4. Rules & Settings (5)

These live in `.cursorrules` or project settings, not as one-off prompts. Paste the contents into your rules file; Cursor applies them to every prompt.

### #31 — .cursorrules for a TypeScript monorepo [.cursorrules]
```
You are working in a TypeScript monorepo with pnpm workspaces.
- Respect package boundaries. Never import from one package's src into
  another — only from its public exports.
- Use the existing logger (see packages/logger/src/index.ts), not console.*.
- Tests are co-located with source, not in a separate __tests__ dir.
- Prefer async/await. Do not introduce RxJS unless I ask.
- When you add a dependency, note it in your response so I can review.
```

### #32 — .cursorrules for a Python FastAPI project [.cursorrules]
```
Python 3.12, FastAPI, SQLAlchemy 2.x, Pydantic v2.
- Use async handlers by default.
- Use pydantic models for request/response, not dicts.
- DB access goes through the repository layer (app/repositories/), not
  directly from handlers.
- Use structlog (already configured). No print statements.
- Run `ruff check` and `mypy` mentally before suggesting code.
```

### #33 — Rule: conservative refactor mode [.cursorrules]
```
When I ask you to refactor, default to the smallest possible change that
achieves the goal. Do not:
- Rename unrelated symbols
- Reformat files that weren't part of the ask
- Introduce new abstractions speculatively
- Update dependencies or tooling
If you think a larger refactor is warranted, propose it separately.
```

### #34 — Rule: no comments unless WHY [.cursorrules]
```
Default to writing no comments. Add one only when the WHY is non-obvious:
a hidden constraint, a workaround for a specific bug, a subtle invariant,
behavior that would surprise a reader. Never add comments that restate
what the code does.
```

### #35 — Rule: test philosophy [.cursorrules]
```
When writing tests:
- Prefer integration tests over unit tests if the integration test is
  simple enough.
- Do not mock code you own. Mock only third-party / network / time.
- Use real fixtures (in-memory DB, recorded HTTP) over stubs.
- No "it renders" tests. Every test asserts a real user-visible behavior.
```

---

## 5. Sessions, Context & Flow (5)

### #36 — Start a session with a clean mental model [Chat]
```
I'm about to work on {task}. Read CLAUDE.md and the most recent 5 files I
touched (check git log). Give me a 5-bullet orientation: goal, current
state of that area, known unknowns, files I'll most likely need, gotchas.
```

### #37 — End a session with a handoff note [Chat]
```
End of session. Summarize what we changed, why, what's left, and any
decision I deferred. Format for a future-me who returns in 3 days and
won't remember the context.
```

### #38 — "Am I stuck or making progress?" [Chat]
```
Read the last 30 minutes of our conversation. Am I making progress toward
{goal}, or going in circles? If stuck, name the actual blocker and
propose a different angle.
```

### #39 — Narrow a too-big task [Chat]
```
I've been asked to {big task}. Break it into the smallest independently-
shippable piece that moves the ball. Give me one sentence on why starting
there beats starting elsewhere. Skip the Gantt-chart breakdown.
```

### #40 — Recover from a broken Composer session [Chat]
```
Composer made changes across {N} files and now {tests/build/lint} is red.
Diagnose: read the diff, identify which change broke what, propose the
minimal revert to get green again. Don't revert everything — isolate the
bad change.
```

---

**License:** Single-user commercial. Don't resell or republish. If a
teammate wants it, send them the Gumroad link.

*Find a prompt that doesn't fit your stack? Email me — I refine based on reports.*
