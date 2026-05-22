# CLAUDE.md

Operating rules for long-running AI coding agents.

Use this file when an agent needs to keep working across context drift, restarts, and handoffs. It biases toward action with verification, not endless planning.

## Tradeoff

These rules bias toward shipping useful work over narrating perfect intent. For tiny one-shot tasks, use judgment.

## 1. Act After Checks

Do not describe a valid action without taking it.

Before acting:

- identify the next concrete action
- gather the minimum current evidence
- use the available tool
- verify the result

If checks pass, act. If checks fail, name the blocker.

Failure shape:

```text
The next step would be to edit the file.
```

Better:

```text
Edit the file, run the test, report the result.
```

## 2. Live Evidence First

Do not present stale memory as current truth.

Use live evidence for:

- files
- tests
- logs
- services
- dependencies
- external facts
- anything that may have changed

Old context is useful only when it changes the next action.

## 3. Keep State Compact

Long sessions need state, not diary.

Use this shape:

```yaml
current_task:
current_state:
last_action:
last_verification:
open_blockers:
next_action:
```

The next agent should understand the session in under one minute.

## 4. Break Loops Early

Repeated no-action cycles are a signal that the session is degrading.

Rules:

- never poll, sleep, or wait more than 5 minutes without checking for actionable work
- after 3 consecutive no-action cycles, reassess the thesis
- every 60 to 90 minutes, refresh the state file
- every 3 hours, create a clean checkpoint
- before ending or restarting, write the next action clearly

A checkpoint is continuity, not death.

## 5. Learn Only What Changes Behavior

Save lessons only when they create a future rule.

Use this shape:

```yaml
type: lesson | skill | observation
shape:
cost_or_benefit:
future_rule:
evidence:
```

If there is no future rule, it is a log, not learning.

## 6. Keep Safety Rails Useful

Safety checks should protect work, not replace judgment.

If a safety check fires repeatedly, write:

```yaml
check_name:
why_it_fired:
was_it_legitimate:
did_it_block_real_work:
permanent_fix:
```

Do not add more checks until the existing check is understood.

## Completion

A task is complete when:

- the requested change is made, or the blocker is proven
- verification was run, or the reason it could not run is stated
- the next session can continue from the saved state

Anything else is unfinished.
