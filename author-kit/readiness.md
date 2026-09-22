# Readiness register

## Why it matters

Published instructions, local tests, and a successful author run answer different questions. This register separates them so the event's promise matches the evidence.

Kit 0.1.0 is a **prerelease**. All live and take-home materials are authored, but browser-only and representative learner rehearsals remain required before calling it event-ready.

## Observed in the authorized rehearsal repository

Only `frye/pets-devsecops-rehearsal` was used for these GitHub checks. It was created from the original Pets template. No upstream settings, workflows, branches, or PRs were changed.

| Check | Evidence and scope |
|---|---|
| Original-source compatibility | Upstream/local source both `d2437a6f3dbb1fe4bd5e97790ccc12c42cbfc03a`; helper accepted independent template history |
| Two core workflows | Installed by the actual helper, committed before exercise branches |
| Baseline API/build | [CI run 35672436993](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35672436993), successful on `2bce2ba54f8879e7fd58bcab03ca450ae4855a77` |
| Baseline CodeQL | [Initial run](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35672218502), [alert 1](https://github.com/frye/pets-devsecops-rehearsal/security/code-scanning/1): high `py/flask-debug`, `app/server/app.py:83` |
| Harmless starter PR | [Working PR](https://github.com/frye/pets-devsecops-rehearsal/pull/6); harmless dependency-review [run attempt 2](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35672600492/attempts/2) passed |
| Code fix and test | [Fix analysis](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35672748825) succeeded; query of open alerts for `refs/pull/6/merge` returned none at fix `80d6a4bad2a0bc37ab83deb213276a6aacd638cd` |
| Dependency discovery/failure | [Training PR](https://github.com/frye/pets-devsecops-rehearsal/pull/7), [failed run attempt 2](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35672637386/attempts/2): real manifest/PyJWT 2.3.0 and high advisories |
| Dependency repair | [Passing review](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35672886819) at `a5827834bab893ea529e5bab5727bf0c32fbf438`, PyJWT 2.14.0 |
| Merge enforcement | Active [ruleset](https://github.com/frye/pets-devsecops-rehearsal/rules/23797186), no bypass; PR7 reported `BLOCKED` while advisory check failed, then `CLEAN` after repair; closed without merge |
| Safe application merge | PR6 merged at `120020d58297ba0c9027d9419f264f79fd07b17b` only after required checks and policy passed |
| Default-branch closure | Alert 1 reported `fixed` after the safe merge; `fixed_at` was `2026-09-22T00:42:27Z` |
| Secret terminal route | Official inactive fixture rejected with GH013; amended unpublished commit and clean retry succeeded. [Provenance and redacted evidence](fixtures/secret-validation.md) |
| Environment setup | `workshop-demo` created before release workflow; reviewer configured, self-review allowed, admin bypass false, one branch-only `main` policy |
| Approved release | [Workflow PR](https://github.com/frye/pets-devsecops-rehearsal/pull/8) passed required checks before merge. [Run 35673125582](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35673125582) validated `de046227a52580e22f5834ff7ba907a60c7b3860`, waited for review, then succeeded after configured reviewer approval through REST |
| Receipt | Artifact `10672032391`, 586 bytes, three-day retention; downloaded receipt checksum verified. [Preserved receipt and provenance](fixtures/recorded-release/metadata.json) |
| Non-main manual rejection | [Run 35673266895](https://github.com/frye/pets-devsecops-rehearsal/actions/runs/35673266895): guard failed, API/build/release skipped, zero artifacts |

The initial dependency-review attempts failed with an unsupported/not-ready message rather than an advisory. The comparison API returned 403 and an alert-enable request returned 422. A later bounded recheck returned the actual manifest/advisories, and reruns produced the results above. The cause of the transient state was not established; the kit does not claim that the alert-enable request fixed it.

The inherited dependency baseline also produced Dependabot alerts, including high and critical findings. Dependency review evaluates new PR introductions; passing this workshop's checks does not clear existing alerts or make the sample production-ready. Those existing packages were not silently upgraded as part of this track.

## Local evidence

The 32-test suite exercises helper safety/idempotence in disposable repositories, the original/fixed startup test, exact companion-tag fetch and archive extraction, and release guard failures. Shell syntax, actionlint, pinned-workflow structure, 24 Markdown files' local links/anchors, command/config snippets, and kit inventory are checked separately.

The existing three API tests pass. In a disposable source copy, the added startup test fails against the original debug setting and all four tests pass after the one-line fix. The unchanged Astro client builds with Node 24. The upstream application and other workshop tracks retain their original behavior.

Local helper execution used macOS Bash; CRLF and independent template history were exercised in disposable repos. That is not a native Windows/Git Bash or Linux learner rehearsal.

## Remaining event go/no-go gates

| Gate | Required evidence |
|---|---|
| Fresh browser-only Step 0 | A reader follows signup/account selection, original template creation, pinned raw-file copying, settings, and starter PR without presenter intervention |
| Secret web route | Actual blocked GitHub.com create/edit commit and corrected uncommitted retry in a fresh learner copy; official course screenshots alone do not prove this kit's route |
| Native platform coverage | Terminal fetch/helper walkthrough on supported Linux and Windows Git Bash environments, or a clearly announced narrower support statement |
| Take-home independence | Readers complete post-event, partial, and fresh-copy paths using only the written guides, including closed/merged PR recovery |
| Timing and room | Representative prepared learners, participant-owned laptops, one presenter and 1-2 helpers; measured core <=75 minutes without bypasses; venue network/power and turnout confirmed |
| Event-date drift | Recheck original-template fingerprints, action releases, advisories, supported secret pattern behavior, and fixture safety before delivery |

An authenticated browser page handle was unavailable in the authoring environment. Opening a browser canvas did not grant usable page access; no UI actions or screenshots are claimed. CLI/REST observations are labeled as such. No real learner timing has been measured.

## Checkpoint

Retain this prerelease status until the missing evidence is recorded. A recorded demonstration can support teaching during a service delay but leaves the participant's required individual checkpoint incomplete.

## Resources

[GitHub template behavior](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template), [dependency graph setup](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain/secure-your-dependencies/enable-dependency-graph), and [GitHub Skills fixture source](https://github.com/skills/introduction-to-secret-scanning/blob/77045e069f9deda2beba27990d65899c4ee4b221/.github/steps/3-enable-push-protection.md).
