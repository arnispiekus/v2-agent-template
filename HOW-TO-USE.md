# Use the working loop

## 1. Morning

Read the project's STATE. Confirm the commit, issue, blocker, owner and next action.
Resolve stale or conflicting state before building.

## 2. Ask for work

Use one issue list as the backlog. State what, why, output, done test and exclusions.
The owner or an explicitly named app assigns agent work. Check raw Markdown for
hidden comments.

## 3. Build

One engine builds within scope. Follow [the loop](playbooks/loop.md),
[test first](playbooks/test-first.md) for behaviour changes and
[find the cause](playbooks/find-the-cause.md) for failures. Stop when authority
or required evidence is missing.

## 4. Check

The other engine reviews the exact commit against the issue and done test. Record
reviewer, model, harness, commit and findings. With one engine, a person checks.
Allow two rounds at most; unresolved findings then go to the owner with one clear
decision. New commits require a new check.

## 5. Prove the outcome

The owner approves merging. Prove with the real person and real data in an
authorised setting. Keep private data out of shared receipts. Record merged,
live and used separately, with evidence and dates. Passing tests and merging do
not establish deployment or acceptance. Could a check pass while the person's
task stays broken?

## 6. End of day

Update STATE with facts, unknowns and the next owner action. Add lessons to MEMORY
and decisions with reasons to DECISIONS. Reconcile TASKS with the issue list;
link issues rather than maintaining another backlog.

## 7. Resume

Answer [the six questions](playbooks/hand-over.md) from files alone. If an answer
depends on old chat, put the missing fact in the appropriate file.

## 8. Weekly review

Spend 30 minutes sampling sessions and receipts. Turn lessons into checks on the
normal path. Verify required checks cannot be skipped under the chosen merge
policy. Prune stale notes and close or rescope stale issues.
