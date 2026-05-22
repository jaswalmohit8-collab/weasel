# Weasel

**One file that stops your AI from talking itself to death.**

Your coding agent after a long context window:

```text
> I should check the test output before continuing.
> Let me think about the best approach.
> Actually, I should verify the state first.
> The next step would be to update the configuration.
```

A lot of words. Zero shipped work.

Weasel is a small public `CLAUDE.md` pattern for long-running AI coding agents. Copy it into a repo, tell the agent to read it, and the session has a simple contract: act when checks pass, verify the result, and keep enough state for the next run.

- [CLAUDE.md](CLAUDE.md) - the copyable operating contract
- [AGENTS.md](AGENTS.md) - compatibility shim for agents that look for `AGENTS.md`
- [DEMO.md](DEMO.md) - a two-minute test prompt
- [demo](demo/) - runtime screenshots

No framework. No server. No hidden system. Just one file you can put in a repo and ask a capable coding agent to follow.

## Try It in 60 Seconds

1. Open Claude, Kimi, ChatGPT, or another capable coding model.
2. Paste the quick-test prompt from [DEMO.md](DEMO.md).
3. Give it a real task.

The shift should show up immediately: fewer status paragraphs, more direct action, clearer blockers.

## Watch It Run

These demos show the same operating pattern under different capable models.

- **60-second demo:** [Edge on Kimi runtime demo](https://www.youtube.com/watch?v=VqFQRd7ud7I)
- **Cross-model demo:** [same operating file across Kimi and Claude](https://youtu.be/0XAs74YT81s)

### What a Real Cycle Looks Like

![Edge agent state after one completed cycle](demo/edge-on-kimi.png?v=2)

The screenshot is not the product. The useful shape is the state packet:

| What appears in the cycle | Why it matters |
|---|---|
| Compact balance/state lines | The agent reports live state instead of narrating intent. |
| Open positions/tasks listed clearly | The next action is grounded in current work, not vague context. |
| Integrity gap called out | The agent names uncertainty instead of hiding it. |
| Rule lapse surfaced | The agent reports process drift before it compounds. |
| Named next condition | The loop pauses only with a reason and a next trigger. |

The point is not the labels in one screenshot. The point is the operating shape: compact, honest, actionable. No filler. No "I should." Just what is true, what happened, and what is next.

## Why This Exists

Long-running agent sessions tend to fail in the same ways:

- context gets heavy and the agent stops seeing the current task clearly
- old notes get treated as live evidence
- plans keep getting rewritten instead of executed
- safety checks become cages instead of useful guardrails
- restarts lose the next action
- "I would do X" replaces doing X

The core rule:

> The context window is working memory, not durable memory. Logs are not learning. A rule only matters if it changes the next action.

## What It Does

`CLAUDE.md` gives an agent six compact rules:

1. act after checks
2. live evidence first
3. keep state compact
4. break loops early
5. learn only what changes behavior
6. keep safety rails useful

The `AGENTS.md` file is only a shim. The canonical rules stay in `CLAUDE.md` so the repo remains simple.

## How To Use It

Copy `CLAUDE.md` into a project where you use a coding agent.

Then start the agent with:

```text
Read CLAUDE.md, then continue this task. Keep state compact and act when checks pass.
```

For long sessions, ask it to maintain a small state file:

```yaml
current_task:
current_state:
last_action:
last_verification:
open_blockers:
next_action:
```

The state file is not a diary. It is a handoff surface.

## What This Is Not

Weasel is not:

- an agent framework
- a benchmark
- a model router
- a desktop assistant
- a claim that a model is conscious
- a replacement for good engineering judgment

It is a small public operating contract for keeping agent work coherent across time.

## Public Boundary

This repo is intentionally small. It does not include private logs, account details, platform automation, internal playbooks, API keys, hidden prompts, or deployment-specific rules.

## Connect

If the operating file lands for your setup, follow along:

- X: [@MohitJaswa27](https://x.com/MohitJaswa27)
- Reddit: [u/Mother-Grapefruit-45](https://www.reddit.com/user/Mother-Grapefruit-45/) and [r/SituationBrief](https://www.reddit.com/r/SituationBrief/)
- Discord: [The Brief](https://discord.gg/H78WYHYThY)

Issues and pull requests are welcome too.

## Credits

Created by MJ with Iris and Cody/Codex. Runtime demos recorded under Kimi Code and Claude Code. Public integrity pass by Raven.

## License

MIT. Copyright (c) 2026 MJ. See [LICENSE](LICENSE).
