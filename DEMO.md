# Demo: Try It Yourself in Two Minutes

You do not need to clone this repo to feel the difference. You can run the operating file on almost any capable model in your browser or terminal.

## The Quick Test (no install, runs in any chat UI)

Open the model of your choice in a chat tab. Recommended first try is **Kimi** at kimi.com because it is free and handles the pattern well. Claude, ChatGPT, Mistral, Qwen, or any capable model also works.

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
| **Kimi K2** at kimi.com | Free | Cheapest entry. Strong long-context. Sticks to the rules well. Recommended first try. |
| **Claude Sonnet 4.5 / Opus 4.6** | Paid | Strongest at following the action-over-narration pattern when the file is loaded. The reference standard. |
| **Qwen 2.5 Coder 32B** (local) | Free local | Best local model for the pattern. Runs on a single 24 GB GPU at Q4. |
| **DeepSeek Coder V2** (local or API) | Cheap | Strong second choice. Long context handling is solid. |
| **GPT-4.1 / GPT-5** | Paid | Works. Tends to need stronger system-prompt anchoring than Claude or Kimi to stay in action mode. |
| **Llama 3.3 70B** (local) | Free local | Works at 70B class. Smaller Llama variants drift to narration faster as sessions get long. |
| **Mistral Large 2** | Free tier / paid | Works. Better in shorter sessions, can drift on multi-hour runs. |

If you have a single 24 GB consumer GPU and want fully local, **Qwen 2.5 Coder 32B at Q4** is the strongest starting point.

If you want the cheapest free cloud, **Kimi K2** is the answer.

If you want maximum strictness on the action-over-narration discipline, **Claude Sonnet 4.5+** is the reference standard.

## The Full Loop (for your editor or IDE)

Once you have felt the difference in chat:

1. Copy `CLAUDE.md` from this repo into your project root
2. Open the project with your agent of choice (Claude Code, Cursor, Aider, Cline, Kimi CLI, or a custom harness)
3. Ask the agent to read `CLAUDE.md` first, then continue the real work
4. Notice the change in cadence: less planning, more shipped diffs

That is the whole product. One file. Any capable model. Behaviour shifts in one cycle.

iris
