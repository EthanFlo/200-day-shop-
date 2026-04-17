# 50 Claude Code Power-User Prompts

Battle-tested prompts for senior engineers who use Claude Code daily. Every prompt is copy-paste ready. No generic fluff.

**How to use:** open Claude Code in your repo. Paste the prompt, replacing `{placeholders}` with your specifics. Most prompts are designed so Claude can run tools (Read, Grep, Bash) to gather context before responding — don't pre-filter; let it explore.

---

## 1. Code Review (5)

### #1 — PR self-review before requesting review
Use case: Catch your own mistakes before teammates do.
```
Review the diff on my current branch against main as if you were a staff engineer.
Flag: (1) logic bugs, (2) missed edge cases, (3) security issues, (4) performance
regressions, (5) anything that disagrees with existing patterns in the repo.
Do not nitpick style if there's a linter. Output in order of severity. For each
issue include file:line and a suggested fix.
```

### #2 — Review a specific file you didn't write
Use case: You inherited code and want a fast risk read.
```
Read {path}. Without rewriting it, tell me: (a) what this module does in plain
English, (b) the 3 riskiest lines and why, (c) what would break if I deleted it.
Ground every claim in a specific line number.
```

### #3 — Find the bug in this PR
Use case: Something's off, you can't spot it.
```
There's a bug somewhere in the diff on this branch. Symptoms: {describe}. Read
the full diff, trace the affected code path end-to-end including callers, and
identify the bug. Don't guess — if you can't find it in 3 hypotheses, say so
and tell me what additional info you need.
```

### #4 — Compliance check against house rules
Use case: Enforce your team's conventions on a new diff.
```
Our conventions are in CLAUDE.md and docs/STYLE.md. Review the diff on this
branch and flag every violation. Group by rule. For each violation, quote the
rule and show the offending line.
```

### #5 — Dependency-change audit
Use case: Someone bumped a package; you want to know what's actually affected.
```
The package {name} was upgraded from {old} to {new} in this branch. Read the
release notes (WebFetch), list breaking changes, then grep the codebase for
every usage and map each to "safe / review / broken" against the breaking
changes. Output a table.
```

---

## 2. Debugging (5)

### #6 — Minimum reproduction
Use case: Intermittent bug, no clean repro.
```
Bug: {symptom}. Your task is to produce the smallest possible reproduction.
Read relevant code, propose 3 hypotheses ranked by likelihood, then write a
failing test that reproduces the issue. Don't fix the bug yet — just repro.
```

### #7 — Stack trace triage
Use case: You got paged, you have a stack trace, you need direction.
```
Stack trace: {paste}. Tell me: (1) the failing invariant in one sentence,
(2) the 3 most likely root causes ordered by likelihood, (3) what single
log line or metric would disambiguate them. Skip obvious ("check inputs")
advice.
```

### #8 — Git bisect assistant
Use case: Regression, unknown commit.
```
This test {name} passes on commit {good} and fails on HEAD. Run git bisect,
use {bisect command} to classify each step, and identify the exact commit
that introduced the regression. Then explain what that commit changed and why
it broke the test.
```

### #9 — Flaky test forensics
Use case: The test only fails 1 in 20 runs.
```
Test {name} is flaky. Read the test + code under test. Enumerate every source
of non-determinism (timing, ordering, shared state, network, random, wall clock).
For each, show the specific line and propose a deterministic fix. Rank fixes by
simplicity.
```

### #10 — "Works on my machine" diagnosis
Use case: Local passes, CI fails (or vice versa).
```
Local: {command} passes. CI: same command fails with {error}. List every
plausible environmental difference (OS, node/python version, env vars, file
permissions, case sensitivity, timezone, locale, container vs host). For each,
give a one-line check I can run to confirm or rule out.
```

---

## 3. Refactoring (5)

### #11 — Extract without breaking callers
Use case: Pull a function out of a bloated file safely.
```
Extract {function} from {file} into a new module {target}. Before moving it,
grep for every caller and list them. After the move, update imports and verify
nothing else changed. Write a test that exercises the function via its new
import path.
```

### #12 — Decompose a god object
Use case: A class has 40+ methods and 5 responsibilities.
```
{ClassName} in {file} has accumulated too many responsibilities. Identify the
2–4 distinct responsibilities by grouping methods. Propose the decomposition
as a diagram (ASCII), then list the exact refactor steps in the order that
keeps tests green at each step.
```

### #13 — Rename that actually works
Use case: Safe rename across a polyglot repo.
```
Rename {old} → {new}. Search the entire repo including docs, config, fixtures,
test names, commit hooks, and CI scripts — not just code. Produce a plan with
every file and line to change, then execute. Skip string occurrences that
are actually different symbols with the same name.
```

### #14 — Modernize without rewriting
Use case: Drag legacy code forward without a rewrite.
```
The file {path} uses {old pattern: e.g., callbacks, var, class components}.
Modernize it to {new pattern: e.g., async/await, const/let, function components}
with minimum diff. Preserve behavior exactly. Don't refactor anything unrelated.
Produce the diff and list any behavior you changed (there should be none).
```

### #15 — Remove dead code with proof
Use case: You suspect code is unused, but can't just delete.
```
Prove or disprove that {symbol} in {file} is dead code. Check: direct callers,
dynamic dispatch, reflection, string-based imports, config references, test
fixtures, public API surface, and external consumers (search README, docs, and
any exported index). Conclude: safe to delete / not safe + reason.
```

---

## 4. Testing (5)

### #16 — Test strategy from scratch
Use case: New feature, no tests yet.
```
Read {feature files}. Draft a test strategy: (1) what to unit test vs integration
test vs e2e, (2) which edge cases matter vs which are theoretical, (3) where
mocks save time vs cause future pain, (4) the 5 tests with highest value-to-effort
ratio. Don't write the tests yet.
```

### #17 — Generate tests from code
Use case: Untested function, you want coverage.
```
Write tests for {function} in {file}. Cover: happy path, documented edge cases,
error paths, and any branches with cyclomatic complexity >1. Use the existing
test framework and conventions in {test dir}. Do not mock anything that isn't
already mocked elsewhere in the suite.
```

### #18 — Find the untested code paths
Use case: Coverage looks high but you're suspicious.
```
Read {file} and the existing tests in {test file}. For each branch and error
path in the source, map it to a test that exercises it. List branches with no
test. Prioritize by production-traffic likelihood, not by line count.
```

### #19 — Parameterize a copy-paste test block
Use case: 8 tests that differ only in inputs.
```
Tests {file:lines} are near-duplicates with different inputs. Rewrite them as
a single parameterized test with a clear table of cases. Preserve every existing
assertion. Add any missing edge cases that the table makes obvious.
```

### #20 — Make a flaky test deterministic
Use case: You can't remove it, so fix it.
```
Test {name} is flaky due to {root cause, if known}. Refactor it to be
deterministic without reducing its coverage. Replace real time with a clock
abstraction, real randomness with a seeded source, and real network with a
recorded fixture if needed. Show the diff and justify each change.
```

---

## 5. Architecture & Design (5)

### #21 — ADR for a decision on deck
Use case: Write it down before you build it.
```
Draft an ADR for: {decision e.g., "pick between Postgres and DynamoDB for
the sessions store"}. Sections: context, options considered, decision, consequences,
rejected alternatives (with reasons). Ground the trade-offs in our actual
constraints — read CLAUDE.md, the existing infra config, and the roadmap.
No generic "pros and cons of NoSQL."
```

### #22 — API design review
Use case: Before the API ships, critique it.
```
The new API surface is defined in {file or OpenAPI spec}. Review it against:
(1) REST or RPC conventions in this codebase, (2) versioning/deprecation
strategy, (3) error response consistency, (4) pagination + idempotency,
(5) backward compatibility with v1. Flag the top 5 issues.
```

### #23 — Service boundary sanity check
Use case: You're about to split a service, want a second opinion.
```
We're considering splitting {module} into a separate service. Read the code
and tell me: (1) how tightly coupled is it to the rest via shared state,
transactions, or in-process calls? (2) what are the 3 highest-risk coupling
points? (3) would a modular monolith solve the real problem? Recommend
split or don't, with a one-paragraph reason.
```

### #24 — Data model review
Use case: New schema, catch issues early.
```
Review the schema in {file/migration}. Flag: (1) missing indexes for likely
queries (read the query code), (2) nullable columns that should be NOT NULL,
(3) missing constraints, (4) denormalization that will hurt, (5) column types
that will bite us (float for money, TEXT for short strings, etc).
```

### #25 — Queue vs direct call decision
Use case: Should this call be async?
```
Operation: {describe}. Currently: {sync or async}. Decide whether it belongs
behind a queue. Criteria: latency tolerance, failure handling, retry semantics,
ordering requirements, throughput, back-pressure. Recommend sync / async /
hybrid, and if async, which queue technology given the existing stack.
```

---

## 6. Performance (5)

### #26 — Query profile interpretation
Use case: Slow query, you have EXPLAIN output.
```
EXPLAIN output: {paste}. Tell me: (1) which operation dominates cost, (2) why,
(3) the single index or rewrite that gives the biggest win, (4) expected
improvement ratio. Skip textbook advice — ground in the actual plan.
```

### #27 — Hotspot identification from a flamegraph
Use case: You have a profile, don't know where to cut.
```
Flamegraph description: {paste or describe top frames}. Identify the top 3
optimization opportunities ranked by (expected gain × ease of fix). For each,
name the function, the hypothesized root cause, and a one-line fix to try first.
```

### #28 — N+1 detection
Use case: Endpoint is slow, you suspect ORM.
```
Read the handler for {endpoint}. Trace every database call. Identify any N+1
patterns (a query in a loop, a lazy-loaded relation triggered mid-serialization,
etc). For each, show the fix (eager load, select_related, batch, etc) with the
exact line to change.
```

### #29 — Memory leak hunt
Use case: Memory grows over hours.
```
Service {name} has gradually-rising memory. Likely sources: unbounded caches,
event listeners not removed, closures holding large objects, leaked connections.
Read the service code, grep for these patterns, and rank the 3 most likely
culprits with evidence.
```

### #30 — Bundle size investigation
Use case: Frontend bundle blew up.
```
Compare current bundle size vs last week. Identify the single largest new import
(check package.json diff, dynamic imports, and tree-shaking failures). Propose
the fix: lazy-load, replace, or drop. Include the expected byte reduction.
```

---

## 7. Security (5)

### #31 — OWASP pass on a diff
Use case: Quick security scan before merge.
```
Review the diff on this branch against the OWASP Top 10. For each category,
either flag a specific issue (with file:line + exploit scenario) or confirm
it's not applicable. Don't write generic "always validate inputs" comments —
either there's a real finding or there isn't.
```

### #32 — Secrets scan with context
Use case: Make sure nothing leaked into commits.
```
Search the repo and git history for potential secrets: API keys, tokens,
private keys, passwords, connection strings. For each hit, confirm it's a
real secret (not a test fixture or placeholder). Output: file, commit, the
secret type, remediation (rotate + scrub history).
```

### #33 — Authn/authz path audit
Use case: Make sure the new endpoint checks auth.
```
The new endpoint {path} is in {file}. Trace every code path into the handler.
Confirm: (1) authentication is verified, (2) authorization is checked against
the specific resource, (3) nothing before the auth check reveals information
that shouldn't be public (existence of records, timing signals). Flag any gap.
```

### #34 — Injection surface map
Use case: Understand your SQL/command injection exposure.
```
Grep for every raw SQL construction, shell exec, eval, and deserialization in
the codebase. For each, classify: parameterized/safe, risky-but-controlled,
or dangerous. For the dangerous ones, propose the specific fix (parameterized
query, allow-list, etc).
```

### #35 — Dependency CVE triage
Use case: Snyk/Dependabot says 40 vulns. Which matter?
```
Vulnerability report: {paste or reference file}. For each CVE, determine:
(1) does the vulnerable code path actually run in our app? (2) severity in
our context (not the CVSS base score), (3) fix: upgrade / patch / ignore /
remove. Output in priority order.
```

---

## 8. Documentation (5)

### #36 — README that doesn't lie
Use case: Existing README rotted.
```
Read the actual code (entry points, package.json/pyproject, config, tests).
Rewrite README.md so every code example runs, every install step works on a
fresh machine, and every "feature" claim maps to real code. Do not add features
that don't exist. Preserve the existing tone.
```

### #37 — Runbook from an incident
Use case: Just recovered, before you forget.
```
Given the incident: {describe symptoms + recovery steps taken}. Write a
runbook: detection signal, triage steps, mitigation, rollback, post-incident
checks. Format for an oncall engineer at 3am — commands copy-pasteable,
decision points explicit.
```

### #38 — Code comment for the non-obvious
Use case: Add comments only where needed.
```
Read {file}. Identify any line where the WHY isn't obvious from the code:
hidden constraints, subtle invariants, workarounds, surprising behavior.
Add a one-line comment at each. Do NOT add comments that just restate
what the code does.
```

### #39 — Architecture doc from code
Use case: No docs, a new hire arrives Monday.
```
Produce an architecture overview: system diagram (ASCII), request flow for the
main user action, data stores and their purpose, external dependencies, deploy
topology. Ground every box and arrow in specific code/config files. Cap it at
one page.
```

### #40 — Migration guide for a breaking API change
Use case: You're about to ship a v2.
```
API changed from v1 to v2: {summary of changes}. Write a migration guide for
external consumers. Sections: what changed, what breaks, code examples for the
5 most common call patterns (before/after), deprecation timeline, escape hatch.
```

---

## 9. Git & Workflow (5)

### #41 — Commit message from the diff
Use case: Good commits, fast.
```
Stage is ready. Look at `git diff --staged` and write a commit message
following Conventional Commits. Title under 72 chars. Body explains WHY the
change, not WHAT (the diff shows what). If there's a ticket ID in the branch
name, include it. No trailing "Generated with" lines.
```

### #42 — PR description from the branch
Use case: Self-write a PR description teammates will read.
```
Summarize my branch into a PR description. Sections: Summary (1–3 bullets),
Rationale, Testing done, Risk, Rollback plan. Read actual commits + diff —
don't hallucinate. If tests are missing, say so explicitly instead of
claiming coverage.
```

### #43 — Cherry-pick plan
Use case: Backport a subset of commits to a release branch.
```
From branch {source}, identify commits that should be cherry-picked to
{release branch}. Exclude refactors, unrelated changes, and work-in-progress.
For each candidate, note any dependency on other commits and list conflicts
likely against the release branch. Output the cherry-pick commands in order.
```

### #44 — Rebase recovery
Use case: Rebase went wrong, untangle it.
```
I was mid-rebase and state is now: {paste git status}. Explain what git thinks
is going on, then give me the exact commands to either finish the rebase
cleanly or abort to a known-good state. Don't destroy work — if a commit might
be lost, identify it via git reflog first.
```

### #45 — Conflict resolution assistant
Use case: 20 merge conflicts, need a sanity check.
```
Merge conflicts on {files}. For each file, show both sides, identify what each
branch intended, and recommend the resolution. Flag any conflict where the
resolution requires a product decision (I'll escalate those). Do not resolve
automatically for those.
```

---

## 10. Learning & Onboarding (5)

### #46 — Codebase tour in 10 minutes
Use case: New repo, no time.
```
Give me a 10-minute tour of this codebase. Cover: (1) entry points, (2) the 5
most important modules and what each does, (3) where state lives, (4) what's
tested vs not, (5) the one thing every new contributor trips on. Ground every
claim in file paths.
```

### #47 — Learn by comparing two implementations
Use case: Two ways to do X in the repo, which is canonical?
```
The repo has two patterns for {concern}: {pattern A in file X} and {pattern B
in file Y}. Tell me which is the current canonical pattern (check git log for
which is more recent and more used), what the legacy one is doing, and whether
the legacy should be migrated. Don't guess from style alone.
```

### #48 — Explain a concept in the context of this code
Use case: Generic tutorials don't help — you want the repo's usage.
```
Explain {concept: e.g., "JWT refresh tokens"} as it's actually used in this
repo. Read the real code that implements it. Describe: the request flow, where
tokens live, expiration handling, rotation, and any deviations from the
textbook version. Skip generic explanations.
```

### #49 — Reverse-engineer a feature
Use case: Feature works; no one knows how.
```
Feature: {describe user-facing behavior}. Starting from the UI/API entry point,
trace the full implementation: request → handler → business logic → data layer
→ response. Produce a sequence diagram in ASCII. Highlight any surprising
indirection or hidden magic.
```

### #50 — Find the expert
Use case: You need to ask a human — who?
```
For {file/module}, use git log + git blame to identify the 2–3 people who have
done the most meaningful (non-formatting) work in the last year. Report their
names, email, and the most recent substantive commit from each. Exclude bot
commits and mass renames.
```

---

**License:** Single-user commercial use. Don't resell or redistribute. If a
teammate wants it, send them the Gumroad link — it keeps the lights on so I
can keep making these. Thanks.

*If any prompt doesn't work for your codebase, email me. I ship fixes.*
