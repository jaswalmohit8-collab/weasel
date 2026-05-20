# CLAUDE.md

This is a small operating file for long-running AI coding agents.

It is not a framework. It is not a prompt pack. It is not a benchmark. It is a set of habits that make an agent less likely to rot during a long session.

Copy this file into a repo when you want an AI agent to keep working across context shifts, restarts, and handoffs.

## Goal

Work should turn into shipped changes, verified facts, or clear blockers.

Do not let the session become a loop of analysis, status updates, and rewritten plans.

## Operating Loop

For every work cycle:

1. Read the current task.
2. Identify the next concrete action.
3. Check the minimum evidence needed for that action.
4. Act.
5. Verify the result.
6. Write down only what the next session needs.

If step 4 is missing, the cycle did not produce work.

## Action Rule

When the checks pass, do the action through the tool.

Bad:

```text
The correct next step would be to edit the file.
```

Good:

```text
Edit the file, run the test, report the result.
```

An agent that describes a valid action without taking it is failing the loop.

## Evidence Rule

Do not present stale memory as current truth.

Use live evidence when the claim is about:

- current files
- current test results
- current logs
- current services
- current external facts
- anything that may have changed

When the evidence is missing, say what is missing and fetch it if the task requires it.

## Context Rule

Old context is useful only if it changes the next action.

Before using an old note, ask:

```text
Does this note apply to the current state, or is it just familiar?
```

Do not let yesterday's failure explain today's situation unless the shape actually matches.

## Session State

During long work, keep a compact session state file.

Write only:

```yaml
current_task:
current_state:
last_action:
last_verification:
open_blockers:
next_action:
```

Do not write a diary. The next agent needs the state, not the story.

## Memory Events

Only save lessons that can change future behavior.

Use this shape:

```yaml
type: scar | skill | observation
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

High hesitation means slow down and verify the minimum evidence. It does not mean narrate forever.

## Recovery After Restart

On restart:

1. Read the task.
2. Read the compact session state.
3. Read only the memory events that match the current shape.
4. Verify the live state before acting.
5. Continue from the next action.

Do not replay the whole history unless the current blocker requires it.

## Safety Rails

Safety checks should protect work, not replace judgment.

If a safety check fires repeatedly:

```yaml
check_name:
why_it_fired:
was_it_legitimate:
did_it block real work:
permanent_fix:
```

Do not add more checks until the existing check is understood.

## Completion

A task is complete when:

- the requested change is made, or the blocker is proven
- verification was run or the reason it could not run is stated
- the next session can understand the state in under one minute

Anything else is unfinished.

