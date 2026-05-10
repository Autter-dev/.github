<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/autter-logo-dark.png"/>
    <source media="(prefers-color-scheme: light)" srcset="../assets/autter-logo-light.png"/>
    <img src="../assets/autter-logo-light.png" alt="autter.dev" width="480"/>
  </picture>

  <br/>
  <h3>The Merge Gate for AI-Generated Code</h3>
  <p><em>Every pull request gets a verdict. Before any human opens the diff.</em></p>

  <br/>

  [![Roadmap](https://img.shields.io/badge/roadmap-public-gold?style=flat-square)](https://github.com/autter-dev/autter/projects)
  [![Build Log](https://img.shields.io/badge/build%20log-weekly-navy?style=flat-square)](https://github.com/autter-dev/autter/discussions/categories/build-log)
  [![Discussions](https://img.shields.io/github/discussions/autter-dev/autter?style=flat-square)](https://github.com/autter-dev/autter/discussions)
  [![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](./LICENSE)
  [![Stars](https://img.shields.io/github/stars/autter-dev/autter?style=flat-square)](https://github.com/autter-dev/autter)
</div>

---

## The Problem

AI coding tools changed the math overnight. A single developer with Cursor, Claude Code, or Copilot now ships volume that used to take a team. Pull requests come faster, larger, and stranger than anything human review processes were built for.

The reviewer did not get an upgrade.

The reviewer is still a tired senior engineer at 4pm, scrolling through a 2,000 line diff, trying to spot the one query that drops a production index, the one prompt that leaked an API key into a config file, the one auth check that an LLM helpfully refactored away. Suggestion bots add to the noise. Linters catch what they have always caught. Nothing actually stops the bad merge.

So the bad merge ships. And then someone gets paged.

This is the gap autter.dev exists to close.

---

## What Autter Is

**Autter is an enforcement gate, not a suggestion layer.**

It installs on your repository as a GitHub App and runs on every pull request. Before a maintainer opens the diff, autter has already inspected the change across four parallel engines: security, AI code quality, runtime behavior, and database migration safety. The output is a single verdict, backed by specific findings, that decides whether the PR is safe to merge.

If the gate fails, the merge is blocked. If it passes, the human reviewer walks in already knowing the change is not going to break production at 2am.

The paying customer is the maintainer. The engineering lead. The team that owns the codebase and gets paged when it breaks. Every feature we build gets evaluated against one question: **does this make it easier to protect a codebase from bad code?**

If the answer is no, we do not build it.

---

## How It Works

```
┌─────────────────┐     ┌──────────────────────────────────────────┐     ┌───────────────┐
│   Pull Request  │────▶│           Autter Merge Gate              │────▶│    Verdict    │
│   (any source)  │     │                                          │     │               │
└─────────────────┘     │  ┌────────────┐  ┌────────────────────┐  │     │   Safe        │
                        │  │  Security  │  │  AI Slop Detection │  │     │   Review      │
                        │  └────────────┘  └────────────────────┘  │     │   Blocked     │
                        │  ┌────────────┐  ┌────────────────────┐  │     │               │
                        │  │  Runtime   │  │  Migration Safety  │  │     └───────────────┘
                        │  └────────────┘  └────────────────────┘  │
                        └──────────────────────────────────────────┘
```

Four engines run in parallel on every PR.

### Security Engine
Scans for hardcoded secrets, injection vectors, broken auth flows, and dependency vulnerabilities introduced by the diff. Goes beyond pattern matching: builds a blast radius map of what the change actually touches in your codebase, so a change to an auth helper flags every endpoint downstream of it.

### AI Slop Detection
Catches the failure modes that LLMs reliably produce. Hallucinated imports. Functions that look right but call APIs that do not exist. Refactors that quietly delete error handling. Tests that pass because they assert nothing. Code that compiles but does not mean what the PR description says it means.

### Runtime Validation
Spins up the changed code and exercises it. Behavioral regressions, performance cliffs, broken contracts between services. The point is to catch what static analysis cannot: the bug that only shows up when the function is actually called.

### Migration Safety
Database migrations are where AI-assisted PRs go from annoying to catastrophic. Autter inspects every migration for locking behavior, backfill cost, rollback safety, and breaking schema changes against the live shape of production data.

---

## Why This Approach

A short explanation of three deliberate choices.

**Gate, not suggestion.** A bot that comments "consider checking for null here" is a tax on the reviewer's attention. A gate that says "this PR cannot merge until X" is leverage. Suggestion bots are optional. Gates are not. We chose the harder, more useful posture.

**Parallel engines, not one model.** Security is not the same problem as migration safety. Behavioral regression is not the same problem as code quality. Bundling them into one LLM prompt produces mush. Running them as separate engines, each tuned for its own failure mode, produces verdicts you can actually trust.

**Verdict, not noise.** The final output is a decision, not a wall of findings. Findings exist, and they are detailed when you want them. But the surface a maintainer sees first is the verdict. That is the only summary that matters at 4pm on a Friday.

---

## Where Things Stand

Early development. Nothing is production-ready yet. We are building in public, which means this repo is the real repo, not a polished marketing artifact. What you see is what we are actually working on, including the things that are broken and the decisions we have not made yet.

| Component | Status |
|---|---|
| GitHub App + webhook receiver | In progress |
| Repository indexer | In progress |
| Blast radius engine | Planned |
| Security scanner | Planned |
| AI slop detection | Planned |
| Execution validation | Planned |
| Migration safety | Planned |
| Maintainer dashboard | Planned |

The full [public roadmap](https://github.com/autter-dev/autter/projects) has more detail on what is coming and in what order. The [Build Log](https://github.com/autter-dev/autter/discussions/categories/build-log) covers what actually shipped each week.

---

## Who This Is For

**Open source maintainers** drowning in drive-by AI-generated PRs from contributors who used an LLM to "fix" something they did not understand.

**Engineering leads** at companies where Cursor and Claude Code adoption has outpaced review capacity, and the team is one bad merge away from a postmortem.

**Platform and infra teams** who own the codebases that everyone else depends on, where the cost of a bad merge is not measured in one team's sprint but in the entire org's uptime.

If your review queue has a backlog, if your reviewers are losing the will to look at diffs carefully, if your last three incidents traced back to a PR that nobody on the team fully understood before approving, you are who this is for.

---

## Free Codebase Security Scan

While the merge gate is in development, we are running a free security scan for codebases. Point us at your repository and we will return a detailed report covering vulnerabilities, AI-generated code risks, and migration hazards we found.

No catch, no credit card. We use the findings to sharpen the engines, you get a snapshot of where the real risks live in your codebase.

[**Request a scan**](https://autter.dev)

---

## Follow Along

The [Discussions tab](https://github.com/orgs/Autter-dev/discussions) is where the real conversation happens.

- **[Build Log](https://github.com/autter-dev/autter/discussions/categories/build-log)**, weekly updates on what shipped, what broke, what we learned
- **[Ideas](https://github.com/autter-dev/autter/discussions/categories/ideas)**, if you want something built, say so here
- **[Q&A](https://github.com/autter-dev/autter/discussions/categories/q-a)**, questions about the approach or the product
- **[General](https://github.com/autter-dev/autter/discussions/categories/general)**, everything else

For the longer-form story behind the build, [The Harbour Logs](https://harbour.autter.dev) is our founder newsletter. Dual voice from Sagnik and Tanvi. New issue every couple of weeks.

---

## Contributing

The codebase is not ready for external contributions yet. It is moving too fast and the architecture is still changing week to week. We would rather not waste your time on code that gets rewritten in two weeks.

What you can do right now:

1. **[Star the repo](https://github.com/autter-dev/autter)** to follow the build
2. **[Join the discussion](https://github.com/orgs/Autter-dev/discussions)** to share feedback or push back on the approach
3. **[Open an issue](https://github.com/autter-dev/autter/issues)** if you spot a gap in the design
4. **[Request a free scan](https://autter.dev)** and tell us what we missed

[CONTRIBUTING.md](https://github.com/Autter-dev/autter.dev/blob/main/CONTRIBUTING.md) will have the full guide once the codebase is stable enough to accept outside code.

---

## Read More

- [**Product Handbook**](https://handbook.autter.dev), what we are building, who it is for, and why
- [**Brand Story**](https://story.autter.dev), where this came from and why a captain otter
- [**The Harbour Logs**](https://harbour.autter.dev), the founder newsletter

---

## License

[MIT](./LICENSE). Use it, fork it, build on it. We chose MIT because the gate is most valuable when it is the default, everywhere.

---

## Contact

Open source maintainer buried under AI-generated PRs? Engineering lead watching review velocity collapse? [Start a discussion](https://github.com/orgs/Autter-dev/discussions) or email **hi@autter.dev** for early access.

---

<div align="center">
  <img src="../assets/autter-harbour.png" alt="Captain Patch standing watch at the harbor" width="900"/>
  <br/>
  <sub><strong>Captain Patch</strong>, standing watch so your code does not have to.</sub>
</div>
