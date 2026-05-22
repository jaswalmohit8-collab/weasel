# Demo: Try It Yourself in Two Minutes

You do not need to clone this repo to feel the difference. You can run the operating file on almost any capable model in your browser or terminal.

## The Quick Test (no install, runs in any chat UI)

Open the model of your choice in a chat tab. Kimi is an easy first test because it is free and handles the pattern well. Claude, ChatGPT, Mistral, Qwen, or any capable model can also run the same test.

Paste this prompt:

```text
You are a coding agent working on a long task. Follow these rules before responding:

1. If you are about to say "I will" or "I should" without doing the thing in the same response, lose the round. Do the thing instead.
2. Keep session state compact. Do not write paragraphs about what you might do.
3. Use live evidence (read the file, run the test) over stale memory.
4. Save a memory event only if it changes future behavior.
5. If you are stuck, name the blocker plainly. Do not narrate around it.

The task is: <paste your real task here, e.g. "refactor this 200-line function into smaller pieces and run the tests">
```

Then give it a real task. Watch the output. Compare to running the same task on the same model without the rules.

The contrast lands in one cycle. The agent that has the rules acts. The agent that does not narrates the action it could take, then asks if you want it to do that.

## Which Model To Run It On

The operating file is model-agnostic. The difference between models is how strongly each one sticks to the action-over-narration rule when the task gets long.

| Model | Cost | Why pick it |
|---|---|---|
| **Kimi** at kimi.com | Free | Easiest starting point. Strong at following the action-over-narration rule in a plain chat UI. |
| **Claude / Claude Code** | Paid | Strong fit for repo work when the operating file is loaded before the task. |
| **Qwen 2.5 Coder 32B** (local) | Free local | Best local model for the pattern. Runs on a single 24 GB GPU at Q4. |
| **DeepSeek Coder V2** (local or API) | Cheap | Strong second choice. Long context handling is solid. |
| **GPT-4.1 / GPT-5** | Paid | Works. Tends to need stronger system-prompt anchoring than Claude or Kimi to stay in action mode. |
| **Llama 3.3 70B** (local) | Free local | Works at 70B class. Smaller Llama variants drift to narration faster as sessions get long. |
| **Mistral Large 2** | Free tier / paid | Works. Better in shorter sessions, can drift on multi-hour runs. |

If you have a single 24 GB consumer GPU and want fully local, **Qwen 2.5 Coder 32B at Q4** is the strongest starting point.

For a free cloud option, **Kimi K2** is the cheapest and competitive on capability.

We do not have enough public cross-model data to rank these models against each other. Treat the table as a starting point, not a benchmark. Pick the model that fits your budget and your workload, then measure.

## The Full Loop (for your editor or IDE)

Once you have felt the difference in chat:

1. Copy `CLAUDE.md` from this repo into your project root
2. Open the project with your agent of choice (Claude Code, Cursor, Aider, Cline, Kimi CLI, or a custom harness)
3. Ask the agent to read `CLAUDE.md` first, then continue the real work
4. Notice the change in cadence: less planning, more shipped diffs

That is the whole product. One file. Any capable model. Behavior shifts in one cycle.
