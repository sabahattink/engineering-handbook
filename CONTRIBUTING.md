# Contributing

Thanks for taking an interest in the Engineering Handbook.

## Scope

This repository documents engineering philosophy and standards. Contributions
are welcome for:

- Fixing errors, ambiguity, or outdated information in existing chapters
- Proposing new chapters or sections that fit the existing structure
- Improving templates once `templates/` is introduced
- Reporting broken links or structural inconsistencies

Contributions that introduce framework- or language-specific guidance into
cross-cutting chapters (e.g. `docs/02-architecture/`) will be redirected —
that kind of content belongs in the specific repository it applies to, not
in this handbook.

## Before opening a pull request

1. Check the chapter's index `README.md` to confirm your change fits its
   stated scope.
2. Keep one logical change per pull request — one chapter or one concern at
   a time.
3. Follow the writing style described in
   [`docs/03-documentation/`](docs/03-documentation/) once that chapter is
   written; until then, match the tone and structure of existing files.
4. Do not add empty placeholder files. If a topic isn't ready to be written,
   note it in the relevant chapter's index `README.md` instead.

## Commit messages

Follow the convention described in
[`docs/04-git-workflow/`](docs/04-git-workflow/) once that chapter is
written. Until then, use clear, imperative-mood commit messages
(e.g. `add release checklist`, not `added stuff`).

## License of contributions

By contributing, you agree that:

- Documentation contributions are licensed under [CC BY 4.0](LICENSES/CC-BY-4.0.txt)
- Template, script, and code contributions are licensed under [MIT](LICENSES/MIT.txt)

See [`LICENSE`](LICENSE) for details.

## Code of Conduct

This project follows the [Code of Conduct](CODE_OF_CONDUCT.md). Participation
implies agreement to its terms.
