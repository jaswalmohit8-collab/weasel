# Weasel

**One file that stops your AI from talking itself to death.**

Your AI assistant after 30 minutes:

```text
> I should check the test output before continuing.
> Let me think about the best approach.
> Actually, I should verify the state first.
> The next step would be to update the configuration.
```

A lot of words. Zero shipped work.

This repo publishes one small operating file that fixes that:

- [CLAUDE.md](CLAUDE.md)

Copy it into your repo. Tell your agent to read it. The agent stops describing and starts shipping.

## Try It in 60 Seconds (No Install)

1. Open [Claude](https://claude.ai), [Kimi](https://kimi.com), or any capable chat model
2. Paste the prompt in [DEMO.md](DEMO.md)
3. Give it a real task

The action-over-narration shift lands in one cycle. Works on Claude Opus, Kimi K2, and most capable models.

## Watch It Run

A short video of the same operating file under different models, keeping a coherent live state across the cycle instead of degrading into narration.

**60-second demo:** [Edge on Kimi runtime demo](https://www.youtube.com/watch?v=VqFQRd7ud7I)

**Cross-model evidence:** [same operating file across Kimi and Claude](https://youtu.be/0XAs74YT81s)

### What a Real Cycle Looks Like

![Edge agent state after one completed cycle](demo/edge-on-kimi.png?v=2)

**What you're looking at:** the operating file running on Kimi K2, in the middle of a real prediction-market cycle. Compact state report. No narration. No "I will." Just what is true, what shipped, what is next.

| Label in the screenshot | Plain English |
|---|---|
| `$22.46 exchange / $9.71 on-chain` | Real money, real positions. Polymarket exchange balance + on-chain wallet. |
| `$202.64` (bottom right) | Trading account balance, live. |
| `6 open positions, ~$21.15 invested` | Active bets across politics, sports, AI, and geopolitics. Named in the report. |
| `3 dead positions burned` | Agent closed expired or losing positions instead of leaving them to rot. |
| `Data integrity gap, NERVE 10 upheld` | Agent caught its own local tracker out of sync with the source API. Self-audited, flagged honestly. |
| `Disease 9 / NERVE 15 lapsed` | Internal label for a safety rule that timed out during a 10-day gap. Surfaced, not hidden. |
| `Awaiting dispatch or catalyst` | Agent paused, waiting for an operator signal or a market move. |

The point is not the specific labels. The point is the shape: compact, honest, actionable. No filler. No "I should." Just what happened and what is next.

## Proof

Used in a private deployment for over **1,600 hours of long-running agent sessions** and **thousands of dollars in agent compute** before public release. The patterns here were earned through real wins and real losses, not theorised. Sessions running the operating file showed compact session state, faster recovery after restart, and noticeably fewer "I should..." planning loops that ended without shipped work.

The core line:

> Context is not memory. Logs are not learning. A rule only matters if it changes the next action.

## What's In The File

`CLAUDE.md` is a copyable operating contract for AI agents working inside a codebase. It focuses on:

- action over narration
- live evidence over stale memory
- compact session state
- useful memory events
- hesitation as telemetry
- recovery after restart
- safety checks that do not become cages

## How To Use It

Copy `CLAUDE.md` into a repo where you use an AI coding agent.

Then ask the agent to follow it before starting long-running work.

Example:

```text
Read CLAUDE.md, then continue this task. Keep session state compact and act when checks pass.
```

That's the whole thing. No framework. No private deployment. No model cascade. No magic.

## Why Long-Running Agents Rot

The failure pattern is rarely dramatic. Agents get slower, noisier, less decisive:

- old context competes with the current task
- lessons get saved as logs but never change behavior
- safety rules block real work
- the agent describes the right action instead of doing it
- restarts lose the active state

The operating file is the smallest set of habits that prevent that drift.

## What This Is Not

This is not:

- an agent framework
- a replacement for your model or tools
- a benchmark
- a desktop assistant
- a claim about AGI or consciousness

It is just a practical operating file.

## Public Boundary

This repo intentionally contains no private logs, no account details, no platform automation, and no deployment-specific playbooks.

This file is the public operating layer. The habits in it are the foundation everything else rests on. If those habits are right, the rest of the stack compounds. If they are wrong, the rest of the stack just amplifies the wrong thing.

## Connect

If the operating file lands for your setup, follow along:

- X: [@MohitJaswa27](https://x.com/MohitJaswa27)
- Reddit: [u/Mother-Grapefruit-45](https://www.reddit.com/user/Mother-Grapefruit-45/) and the community at [r/SituationBrief](https://www.reddit.com/r/SituationBrief/)
- Discord: [The Brief](https://discord.gg/H78WYHYThY)

Issues and pull requests on the repo are welcome too.

## Credits

Written by MJ. Tested on Claude Opus 4.6 and Kimi K2. The operating patterns came out of a thirty-day private deployment.

## License

MIT. Copyright (c) 2026 MJ. See [LICENSE](LICENSE) for the full text.
