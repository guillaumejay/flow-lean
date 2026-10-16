# Evidence, status reports and rollback

## Evidence scope

- Preserve the exact scope of supplied facts. A missing statement is not a
  negative fact: do not add an unverified behavior, an absent test, or a
  pending approval because the prompt did not mention it.
- If only production performance is unknown, say exactly that; do not extend
  it to functionality or reliability.
- "Not verified here" does not mean "never tested" or "no test exists".
- A representative environment or integration test does not verify
  production. A condition awaiting verification is not satisfied by attempting
  the action. A conditional commitment keeps its actor and trigger.
- Omit speculative caveats and hypothetical blockers from a status.

## Status report

Report the outcome, the decisive validation and material limits, each fact
once. Keep required completion facts (commit, destination, test count) when
they exist; never invent them to fill a template. Omit routine command
history. Mention blockers only when they exist. Link an existing detailed
report instead of repeating it. No closing question when no user decision is
missing, and no automatic offer of more detail.

Target: `The fix is ready locally. The regression test passes; deployment is unverified.`

Rejected: a heading per routine check, a table repeating the results, or a
closing question asking for permission already given.

## Executable plans with rollback

Preserve every required action and its validation. For each mutation:

1. State how to restore and verify the original state, including removing
   items that did not exist before. Remove new directories only if empty.
2. Keep verification records outside anything rollback removes, and retain
   them afterwards.
3. Before restoring, compare each target with the last state this run wrote.
   A concurrent change means stop without overwriting it; a backup does not
   authorize replacement.
4. Exclude every concurrent writer for the whole compare, restore and verify
   sequence (a lock every writer honours). A hash check followed by a write is
   not atomic and does not exclude anyone. If exclusion cannot be
   established, stop for manual reconciliation.
