# Engineering Handbook

The engineering operating system behind every public repository in the
Sabahattin Kalkan ecosystem — engineering philosophy, decision-making,
repository and architecture standards, workflow, review, release, security,
and maintenance practices, all in one canonical place.

This is not a company or team handbook. It is a personal, public reference
for how I design repositories, make engineering decisions, write and review
code, ship releases, and maintain open-source projects long-term. The
audience is myself (future reference), contributors to my projects, and
anyone interested in the reasoning behind how they're built.

Every public repository under this ecosystem is expected to follow this
handbook instead of redefining its own rules.

## How to reference this handbook

Repositories must **not** link here with relative paths (`../engineering-handbook/...`).
Always link to a canonical GitHub URL so the reference works regardless of
where the other repository lives on disk or how it's cloned:

```
https://github.com/sabahattink/engineering-handbook/blob/main/docs/<chapter>/<file>.md
```

Example — referencing the commit convention from another repo's `CONTRIBUTING.md`:

```markdown
This project follows the
[commit conventions](https://github.com/sabahattink/engineering-handbook/blob/main/docs/04-git-workflow/commit-conventions.md)
defined in the Engineering Handbook.
```

## Structure

The handbook is organized into numbered chapters under [`docs/`](docs/). The
numbering defines reading order and leaves room for future chapters without
renumbering existing ones.

| Chapter | Topic |
|---|---|
| [`00-philosophy`](docs/00-philosophy/) | Engineering principles, decision-making framework, explicit non-goals |
| [`01-repository-standards`](docs/01-repository-standards/) | Repo structure, naming, README standards |
| [`02-architecture`](docs/02-architecture/) | Cross-cutting architectural principles (framework-agnostic) |
| [`03-documentation`](docs/03-documentation/) | Writing style, documentation types, diagrams |
| [`04-git-workflow`](docs/04-git-workflow/) | Branching strategy, commit conventions, PR process |
| [`05-code-review`](docs/05-code-review/) | Review principles, checklist, severity levels |
| [`06-testing`](docs/06-testing/) | Testing philosophy, coverage standards, test pyramid |
| [`07-release-process`](docs/07-release-process/) | Versioning, release checklist, changelog standards |
| [`08-automation`](docs/08-automation/) | CI/CD standards, tooling |
| [`09-ai-usage`](docs/09-ai-usage/) | Principles for AI-assisted engineering and AI-generated code review |
| [`10-security`](docs/10-security/) | Security principles, secret management, vulnerability response |
| [`11-maintenance`](docs/11-maintenance/) | Long-term maintenance, deprecation policy, issue triage |
| [`12-adrs`](docs/12-adrs/) | Architecture Decision Records |

Reusable, machine-consumable templates (README, ADR, PR, issue, checklist
templates) live at the repository root in `templates/`, separate from
`docs/`, so automation and repository scaffolding tools can consume them
directly. This directory is introduced in a later chapter.

Each chapter directory currently contains an index `README.md` describing
its scope and planned contents. Chapters are being written one at a time —
see status below.

## Status

This handbook is under active construction. Chapter 0 (this README,
repository skeleton, contribution/security/license documentation) is
complete. Chapter content (00 through 12) is written incrementally.

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Security

See [`SECURITY.md`](SECURITY.md).

## License

Dual-licensed — see [`LICENSE`](LICENSE).
