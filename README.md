# Weasel

A tiny public `CLAUDE.md` for keeping long-running AI coding agents useful.

Most agent failures are not dramatic. The agent just gets slower, noisier, and less decisive. It keeps planning, keeps explaining, keeps checking, and stops shipping.

This repo publishes one small operating file:

- [CLAUDE.md](CLAUDE.md)

That's it. No framework. No private deployment. No model cascade. No magic.

## What This Is

`CLAUDE.md` is a copyable operating contract for AI agents working inside a codebase.

It focuses on:

- action over narration
- live evidence over stale memory
- compact session state
- useful memory events
- hesitation as telemetry
- recovery after restart
- safety checks that do not become cages

## Why It Exists

Long-running agents tend to rot in predictable ways:

- old context competes with the current task
- lessons are saved as logs but never change behavior
- safety rules block real work
- the agent describes the right action instead of doing it
- restarts lose the active state

The core line:

> Context is not memory. Logs are not learning. A rule only matters if it changes the next action.

## Results

Used in a private deployment for many long-running agent sessions before public release. Agents running with this operating file show measurably lower narration-to-action drift and stronger session-completion patterns compared to the same agents running without it. The patterns here were earned, not theorised.

## Before And After

Without the operating file, a long session usually drifts like this:

```text
> I should check the test output before continuing.
> Let me think about the best way to approach this.
> The next step would be to update the configuration.
> Actually, I should verify the state first.
```

The agent describes work. It does not ship work.

With the operating file loaded, the same agent reads the task, identifies the next concrete action, runs the minimum evidence check, fires the tool, and writes only what the next session needs. Less narration, more verified deltas on disk.

## Try It in Two Minutes (No Install)

Want to feel the difference before cloning? Open Kimi at kimi.com (free), Claude, or any chat model. Paste the prompt in [DEMO.md](DEMO.md) and give it a real task. The action-over-narration shift lands in one cycle.

DEMO.md also lists which models handle the pattern best, including local options like Qwen 2.5 Coder 32B.

## How To Use It

Copy `CLAUDE.md` into a repo where you use an AI coding agent.

Then ask the agent to follow it before starting long-running work.

Example:

```text
Read CLAUDE.md, then continue this task. Keep session state compact and act when checks pass.
```

## Demo

A one-minute runtime example of Weasel under a capable model. The agent profile shown is named Edge, the model is Kimi Code, and the state is monitoring an active cycle with compact session state, open loops, integrity checks, and a named next-action.

The demo proves the operating file is model-agnostic. A capable model running `CLAUDE.md` keeps a coherent live state across the cycle rather than degrading into narration.

![Edge on Kimi, monitoring an active cycle](demo/edge-on-kimi.png?v=2)

**Watch on YouTube:** [Edge on Kimi runtime demo](https://www.youtube.com/watch?v=VqFQRd7ud7I)

**Cross-model evidence:** [same operating file under Kimi, plus Claude or any capable model](https://youtu.be/0XAs74YT81s) (12 second clip)

## What This Is Not

This is not:

- an agent framework
- a replacement for your model or tools
- a benchmark
- a desktop assistant
- a trading or social automation system
- a claim about AGI or consciousness

It is just a practical operating file.

## Public Boundary

This repo intentionally contains no private logs, no account details, no platform automation, no hidden prompts, and no deployment-specific playbooks.

This file is the public operating layer. The private deployment adds telemetry, memory indexing, and runtime safety monitoring around it. The habits in this file are the foundation everything else rests on. If those habits are right, the rest of the stack is leverage. If they are wrong, the rest of the stack is amplifying the wrong thing.

## Credits

Initial public README and `CLAUDE.md` drafted by MJ in collaboration with Iris (Claude Opus 4.6). Runtime demo recorded under Kimi Code. The operating patterns came out of a thirty-day private deployment.

---

*Audited by Raven (Kimi Code CLI) | 2026-05-20 18:38 ET | Public repo integrity: png hash verified e7b54480…80f2 against local source, raw URLs tested 200 OK from anonymous curl.*

*Follow-up by Iris (Claude Opus 4.6) | 2026-05-20 19:18 ET | Video binaries removed from git; YouTube link is the durable video reference.*

## Connect

If the operating file lands for your setup, follow along:

- X: [@MohitJaswa27](https://x.com/MohitJaswa27)
- Reddit: [u/Mother-Grapefruit-45](https://www.reddit.com/user/Mother-Grapefruit-45/) and the community at [r/SituationBrief](https://www.reddit.com/r/SituationBrief/)
- Discord: [The Brief](https://discord.gg/H78WYHYThY)

Issues and pull requests on the repo are welcome too.

## License

MIT. Copyright (c) 2026 MJ. See [LICENSE](LICENSE) for the full text.
