# 01 — Repository Standards

This chapter defines the minimum auditable standard for public repositories.
Unless a rule names another scope, it applies to every CORE repository.

A repository passes this standard only when every applicable requirement is
satisfied. Evidence may come from the default branch, repository settings,
release metadata, and package registries. Planned work does not count as
compliance unless the rule explicitly permits a documented plan.

## Repository Purpose

The repository must state:

- the problem it solves;
- the intended user;
- the supported use cases;
- the explicitly unsupported use cases;
- the relationship to overlapping repositories in the same ecosystem.

These statements must appear in `README.md` before installation instructions.
The purpose fails audit if it is only a technology description, contains no
intended user, or conflicts with the implemented behavior.

## Maturity Levels

Every repository must declare exactly one maturity level in `README.md`:

| Level | Entry Criteria | Release Constraint |
|---|---|---|
| `EXPERIMENTAL` | Interface and scope may change without migration support | Must not publish a stable release |
| `ALPHA` | Primary workflow runs; known missing behavior is documented | Version remains below `1.0.0` and uses a prerelease identifier when released |
| `BETA` | Intended scope is implemented; compatibility is still being validated | Version remains below `1.0.0` or uses a prerelease identifier |
| `STABLE` | Public interfaces, tests, documentation, and release process satisfy this chapter | Stable releases use `1.0.0` or later |

A maturity change must include the evidence that satisfies the destination
level. A label alone does not change maturity.

## Ownership

Each repository must identify:

- one accountable owner by GitHub handle;
- the package or release owner when different from the GitHub owner;
- the next review date in `YYYY-MM-DD` format.

Ownership must appear in `README.md` or `MAINTAINERS.md`. Package manifests,
release metadata, badges, and repository URLs must resolve to the same owner or
document why they differ.

Administration and publishing access must be verified through authenticated
owner confirmation. Without that confirmation, ownership is `UNVERIFIED` and
fails audit.

## Repository Status Labels

Every repository must declare exactly one operational status:

| Status | Meaning |
|---|---|
| `ACTIVE` | Feature development is planned and maintained |
| `MAINTENANCE` | Only fixes, dependency updates, and bounded improvements are planned |
| `SECURITY_ONLY` | Only supported security fixes are planned |
| `DEPRECATED` | Users are expected to migrate before a stated date |
| `ARCHIVED` | No support or development is planned |

The status must appear before the first second-level heading in `README.md`.
The GitHub description, repository archive setting, package deprecation state,
and README must not contradict it.

## Required Documentation

The default branch must contain:

- `README.md`;
- a license file accepted by the policy below;
- `SECURITY.md`;
- contribution instructions in `CONTRIBUTING.md` or a linked handbook section;
- a changelog when the changelog policy applies;
- architecture documentation when the repository has more than one deployable
  component or public integration boundary;
- migration documentation for every breaking release;
- an explicit testing plan when automated tests do not yet exist.

Documentation must describe the current default branch. Commands must be
executable as written from a clean clone in a supported environment.

## README Standard

`README.md` must contain these sections in this order unless a section is not
applicable:

1. repository name and one-sentence purpose;
2. maturity and operational status;
3. ownership;
4. supported and unsupported use cases;
5. requirements;
6. installation;
7. minimum working example;
8. configuration, including required environment variables without values;
9. test and validation commands;
10. release or package status;
11. security-reporting link;
12. license;
13. next milestone.

The README fails audit when:

- a local asset or link does not resolve;
- a badge points to another repository or owner without explanation;
- installation depends on an undocumented step;
- examples use an API that the default branch does not provide;
- a future feature is described as available;
- maintenance, release, compatibility, performance, security, usage, or
  adoption claims have no cited evidence;
- the declared status conflicts with repository or package state.

Accepted evidence is repository or release metadata for maintenance and
release claims, passing compatibility tests for compatibility claims,
reproducible benchmark results for performance claims, security scan or
advisory records for security claims, and package-registry or GitHub records for
usage and adoption claims.

## License Policy

Every public repository must include a root license file before its first
public release.

- Source code must use an OSI-approved license unless a documented exception
  states why redistribution is restricted.
- Documentation and media with a different license must identify that license
  and the files it covers.
- `package.json`, package metadata, generated headers, and README license text
  must agree with the root license.
- Third-party material must retain its original attribution and license.
- A repository with unknown or incompatible third-party licensing cannot be
  released.

Changing a license requires an ownership review of all contributed code before
the change is accepted.

## CHANGELOG Policy

`CHANGELOG.md` is required when a repository publishes versioned releases or
packages for external use.

It must:

- contain an `Unreleased` section;
- group entries under `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, or
  `Security`;
- link or name every released version and date;
- identify breaking changes and link their migration instructions;
- exclude internal refactors with no user-visible effect.

The release diff and changelog must agree before a release is created.

## Versioning

Versioned public interfaces must follow Semantic Versioning.

- `MAJOR` changes break a documented public interface.
- `MINOR` changes add backward-compatible behavior.
- `PATCH` changes are backward-compatible fixes.
- Prerelease versions use a SemVer prerelease identifier.
- Published tags use `v<version>` and match package or binary metadata exactly.
- A version must never be reused or moved to another commit.

Public interfaces include command syntax, configuration keys, exported APIs,
network protocols, file formats, and documented automation behavior.

## Release Policy

A release may be created only when:

- the release commit is on the default branch;
- required CI checks pass on that commit;
- the version and tag agree;
- the changelog contains the release date and user-visible changes;
- breaking changes include migration instructions;
- distributable artifacts are built from the tagged commit;
- artifact checksums or package-registry provenance are available when the
  distribution channel supports them;
- no unresolved known critical vulnerability affects the released path.

Each release must publish notes that link to the changelog and identify the
supported maturity level.

## Branch Strategy

The default branch must be `main`.

- `main` must remain releasable or explicitly carry a prerelease maturity
  label.
- Work branches must be short-lived and scoped to one reviewable change.
- CORE repositories must merge changes through pull requests.
- Required CI must pass before merge.
- Force-pushes to `main` are prohibited.
- Release branches are permitted only when a supported older major version
  requires fixes; the supported version and end date must be documented.
- Stale branches must be deleted after merge or closure unless they preserve a
  supported release line.

## Testing Expectations

Each repository must list its primary workflows and critical behaviors in
`README.md` or testing documentation. Every change to a listed workflow or
behavior must include an automated test that can detect its regression.

CORE repositories must provide:

- one documented non-interactive test command;
- tests for the primary user workflow;
- tests for public interfaces and documented failure behavior;
- a regression test for every corrected defect when reproducible;
- isolated tests that do not require production credentials;
- an explicit integration-test boundary for external services;
- no unexplained skipped, focused, or quarantined test in the default branch.

If automated tests do not yet exist, the repository cannot be `STABLE`. Its
README must link an owner, scope, and completion criterion for the testing plan.

Coverage percentage alone does not satisfy this standard. The audit maps every
listed primary workflow and critical behavior to a corresponding test or
documented testing-plan entry.

## CI Expectations

CI must run on every pull request and every push to `main`.

The required pipeline must, where applicable:

1. install dependencies from the committed lockfile without updating it;
2. validate formatting or lint rules;
3. type-check compiled languages that support a separate check;
4. run automated tests;
5. build distributable output;
6. validate generated files are current;
7. perform dependency and secret scanning.

CI must fail when a required step fails. Required jobs must not use
`continue-on-error`. Actions and reusable workflows must be pinned to a major
release or immutable commit. Workflow permissions must be the minimum required
for the job.

## Dependency Policy

Every repository must:

- commit exactly one lockfile for each package ecosystem in use;
- declare the package-manager and runtime versions used by CI;
- remove unused direct dependencies;
- keep runtime and development dependencies correctly separated;
- record the reason for any dependency that has no maintained release or has a
  single point of maintainer failure;
- review automated dependency updates through the normal test and CI path;
- review direct dependencies and known vulnerabilities at least once every 90
  days while status is `ACTIVE` or `MAINTENANCE`.

A new runtime dependency must identify the capability it replaces and pass
license and vulnerability checks before merge.

## Security Policy

`SECURITY.md` must state:

- supported versions;
- a private reporting channel;
- the information required in a report;
- the expected acknowledgement window;
- the disclosure process.

CORE repositories must also:

- run secret scanning on pull requests and `main`, with no unresolved detected
  secret;
- run dependency vulnerability scanning in CI or an enabled repository
  service;
- document credential and sensitive-data handling;
- use least-privilege workflow permissions;
- exclude real secrets from examples, fixtures, logs, and generated assets;
- record an owner and remediation decision for every open high or critical
  vulnerability.

A stable release cannot proceed with an unresolved critical vulnerability in a
released code path.

## Maintenance Policy

The declared operational status determines the required activity:

| Status | Required Activity |
|---|---|
| `ACTIVE` | Triage new issues and security reports within 14 calendar days; review dependencies every 90 days |
| `MAINTENANCE` | Triage defects and security reports within 30 calendar days; review dependencies every 90 days |
| `SECURITY_ONLY` | Respond only to supported security reports within the window stated in `SECURITY.md` |
| `DEPRECATED` | Apply the documented support policy until the stated end date |
| `ARCHIVED` | No support or development is planned |

At least once every 90 days, the owner must verify repository status, supported
versions, open security findings, release state, and next milestone. The review
result and date must be recorded in `README.md` or `MAINTENANCE.md`, including
the next review date, even when no change is required.

If the owner cannot meet the declared commitment, the status must change before
the response window is missed repeatedly.

## Archival Policy

A repository must be considered for archival when any of these conditions is
true:

- no owner accepts the maintenance commitment;
- the original problem no longer exists;
- another maintained repository supersedes it;
- required dependencies or platforms are no longer supportable;
- unresolved security risk exceeds the repository's value;
- the repository has no verified use and no planned milestone.

Before archival:

- [ ] Confirm no supported package, deployment, documentation, or repository
      depends on continued development.
- [ ] Preserve source and release history.
- [ ] Publish a final status notice at the top of `README.md`.
- [ ] Name the successor and migration path when one exists.
- [ ] Deprecate published packages when the registry supports it.
- [ ] Close or transfer unresolved work with an explicit disposition.
- [ ] Disable workflows that write, publish, deploy, or rotate credentials.
- [ ] Remove active-support claims and badges.
- [ ] Enable the GitHub archive setting.

Deletion requires a separate decision after archival checks confirm that no
source, history, package, link, or user dependency must be preserved.

## CORE Repository Audit Checklist

A CORE repository passes Chapter 01 only when all applicable checks pass:

- [ ] Purpose, intended user, supported scope, and unsupported scope are stated.
- [ ] Exactly one maturity level and one operational status are visible.
- [ ] GitHub, package, release, and maintenance ownership are explicit.
- [ ] The operational status and next review date are current.
- [ ] Required documentation exists and describes the default branch.
- [ ] README commands work from a clean clone.
- [ ] License and third-party attribution are consistent.
- [ ] Changelog, version, tag, and release metadata agree.
- [ ] `main` is the default branch and required CI protects merges.
- [ ] Primary workflows and public interfaces have automated tests or an
      explicit incomplete testing plan.
- [ ] CI installs deterministically and runs every applicable required check.
- [ ] Dependencies are locked, reviewed, licensed, and vulnerability-scanned.
- [ ] Security reporting, supported versions, secrets, and workflow permissions
      satisfy the security policy.
- [ ] Repository status matches actual maintenance behavior.
- [ ] Archive criteria have been evaluated and no criterion requiring action is
      unresolved.

An audit result must record `PASS`, `FAIL`, or `NOT APPLICABLE` for every item.
`NOT APPLICABLE` requires a written reason. A repository with any `FAIL` does
not satisfy the Chapter 01 standard.
