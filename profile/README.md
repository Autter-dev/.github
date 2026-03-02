<div align="center">
 <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/autter-logo-dark.png"/>
    <source media="(prefers-color-scheme: light)" srcset="../assets/autter-logo-light.png"/>
    <img src="../assets/autter-logo-light.png" alt="autter.dev" width="480"/>
  </picture>
  <br/><br/>

[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](./LICENSE)
[![Roadmap](https://img.shields.io/badge/roadmap-public-gold?style=flat-square)](https://github.com/autter-dev/autter/projects)
[![Discussions](https://img.shields.io/github/discussions/autter-dev/autter?style=flat-square)](https://github.com/autter-dev/autter/discussions)

</div>

---

AI coding tools let developers ship ten times more code. Human reviewers have not scaled to match.

autter.dev is the merge gate that closes that gap. It installs on your repository and runs on every pull request. Every merge gets a verdict before any human opens the diff.

> **Building in public.** This is the real repo, not the marketing site. What you see here is what we are actually working on, including the things that are broken and the decisions we have not made yet.

---

## What It Does

Every pull request gets checked for security vulnerabilities, AI-generated code quality issues, behavioral regressions, and database migration safety, before it can merge. Maintainers get a clear risk verdict and actionable findings instead of an inbox full of noise.

The paying customer is the maintainer or engineering team, not the contributor. Every feature we build is evaluated against one question: does this make it easier to protect a codebase from bad code?

---

## Where Things Stand

Early development. Nothing is production-ready yet. The status table below is updated as things ship.

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

The full [public roadmap](https://github.com/autter-dev/autter/projects) has more detail on what is coming and in what order.

---

## Follow Along

The [Discussions tab](https://github.com/orgs/Autter-dev/discussions) is where the real conversation happens:

- **[Build Log](https://github.com/autter-dev/autter/discussions/categories/build-log)** — weekly updates on what shipped, what broke, and what we learned
- **[Ideas](https://github.com/autter-dev/autter/discussions/categories/ideas)** — if you want something built, say so here
- **[Q&A](https://github.com/autter-dev/autter/discussions/categories/q-a)** — questions about the approach or the product
- **[General](https://github.com/autter-dev/autter/discussions/categories/general)** — everything else

---

## Contributing

The codebase is not ready for external contributions yet. It is moving too fast and the architecture is still changing week to week.

What you can do right now:

- **[Star the repo](https://github.com/autter-dev/autter)** to follow the build
- **[Join the discussion](https://github.com/orgs/Autter-dev/discussions)** to share feedback or push back on the approach
- **[Open an issue](https://github.com/autter-dev/autter/issues)** if you spot a gap in the design

[CONTRIBUTING.md](./CONTRIBUTING.md) will have the full guide once the codebase is stable enough to accept outside code.

---

## Read More

- [Product Handbook](https://handbook.autter.dev) — what we are building, who it is for, and why
- [Brand Story](https://story.autter.dev) — where this came from

---

## License

[MIT](./LICENSE)

---

## Contact

If you are an open source maintainer drowning in AI-generated PRs and want early access, [start a discussion](https://github.com/orgs/Autter-dev/discussions).

---

<div align="center">
  <img src="../assets/autter-harbour.png" alt="Captain Patch standing watch at the harbor" width="900"/>
  <br/>
  <sub>Captain Patch — standing watch so your code does not have to.</sub>
</div>
