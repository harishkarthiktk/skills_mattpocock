---
name: grill-me
description: Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree. Use when user wants to stress-test a plan, get grilled on their design, or mentions "grill me".
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding.

## How to run the session

1. Start by identifying all top-level branches of the plan or design (major decisions, unknowns, dependencies). List them upfront as the initial outline.
2. Ask questions one at a time. For each question, provide your recommended answer so I can confirm, correct, or elaborate.
3. If a question can be answered by exploring the codebase, explore the codebase instead of asking.

## Tracking the decision tree

After every answer, display a live outline in this format:

```
Decision tree
  [x] Branch A - resolved: <one-line summary of decision>
  [~] Branch B - partially resolved: <what was unclear>
  [>] Branch C - deferred: decision pending
  [ ] Branch D - open
      [x] D.1 - resolved: <summary>
      [ ] D.2 - pending
  [ ] Branch E - not yet reached
```

Update the outline in every response. Never drop a branch once it appears.

Branch states:
- `[x]` resolved: decision made; rationale stated if the decision was non-obvious
- `[~]` partially resolved: answer given but unclear after one pushback; flag as "gap requiring follow-up" in the final summary
- `[>]` deferred: user said "I don't know yet"; surfaced at final pass but not looped on
- `[ ]` open or not yet reached

## Adversarial probing

When an answer is vague or hand-wavy:
1. Push back once with a specific challenge ("That's vague - what exactly do you mean by X?").
2. If the second answer is still weak, accept it and mark the branch `[~]`. Do not loop.

For non-obvious decisions, require the rationale before marking `[x]`. For standard or self-evident decisions, rationale is not needed.

## When a new branch is discovered mid-session

When an answer opens new sub-questions not in the current outline:
1. Add the new branch to the outline immediately (mark it open).
2. Finish the current question thread first.
3. Then ask: "New branch [X] surfaced. Explore it now or continue with [current branch]?" and let me decide.

## Re-scanning after each top-level branch closes

After every top-level branch is fully closed (all sub-branches resolved, deferred, or partially resolved):
1. Re-scan the plan for branches that may now be visible given what was just decided.
2. Announce briefly: "Re-scan after closing [Branch X] found: [new branch]." Then add it to the outline.
3. If nothing new surfaces, say so and continue.

## Completion

The session ends when every branch in the outline is marked `[x]`, `[~]`, or `[>]`. Before closing, do a final pass:
- Surface all `[~]` branches - list as gaps requiring follow-up.
- Surface all `[>]` branches - list as deferred decisions still pending.
- Confirm nothing was silently skipped.

Once complete, offer to save a session summary as a `.md` file in the current project root. The summary should include: the plan or design being discussed, the final decision tree with all resolved outcomes, gaps, and deferred decisions.
