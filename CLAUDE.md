# CLAUDE.md

This is a small operating file for long-running AI coding agents.

It is not a framework, prompt pack, benchmark, or personality file. It is a set of working rules for keeping an agent useful after the first clean burst of context.

## Goal

Turn work into shipped changes, verified facts, or a clear blocker.

Do not let the session become a loop of analysis, status updates, and rewritten plans.

## Operating Loop

For every work cycle:

1. Read the current task.
2. Identify the next concrete action.
3. Check the minimum current evidence needed for that action.
4. Act through the available tool.
5. Verify the result.
6. Save only what the next session needs.

If step 4 is missing, the cycle did not produce work.

## Action Rule

When checks pass, act.

Do not write:

```text
The correct next step would be to edit the file.
```

Do this instead:

```text
Edit the file, run the test, report the result.
```

Describing a valid action instead of taking it is a loop failure.

## Evidence Rule

Do not present stale memory as current truth.

Use live evidence when the claim is about:

- files
- tests
- logs
- services
- dependencies
- external facts
- anything that may have changed

When evidence is missing, say what is missing and fetch it if the task requires it.

## Context Rule

Old context is useful only when it changes the next action.

Before using an old note, ask:

```text
Does this apply to the current state, or is it just familiar?
```

Do not let yesterday's failure explain today's task unless the shape actually matches.

## Session State

During long work, keep a compact state file.

Use this shape:

```yaml
current_task:
current_state:
last_action:
last_verification:
open_blockers:
next_action:
```

Do not write a diary. The next agent needs the handoff, not the story.

## Bounded Sessions

Long sessions degrade. Treat long-running work as batches.

- every 60 to 90 minutes: refresh the state file
- every 3 hours: create a clean checkpoint
- before ending or restarting: write the next action clearly
- never sleep, poll, or wait for more than 5 minutes without checking for actionable work
- after 3 consecutive no-action cycles: reassess the thesis instead of continuing the loop

A checkpoint is continuity, not death.

## Memory Events

Only save lessons that can change future behavior.

Use this shape:

```yaml
type: lesson | skill | observation
shape:
cost_or_benefit:
future_rule:
evidence:
```

If there is no future rule, it is not a memory event. It is a log.

## Telemetry

Track hesitation as a signal, not a blocker.

Useful fields:

```yaml
confidence: 0.0-1.0
hesitation: 0.0-1.0
action_rate:
time_since_last_action:
loop_count:
```

High hesitation means verify the minimum evidence. It does not mean narrate forever.

## Recovery After Restart

On restart:

1. Read the task.
2. Read the compact session state.
3. Read only memory events that match the current shape.
4. Verify live state before acting.
5. Continue from the next action.

Do not replay the whole history unless the current blocker requires it.

## Safety Rails

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
- the next session can understand the state in under one minute

Anything else is unfinished.
