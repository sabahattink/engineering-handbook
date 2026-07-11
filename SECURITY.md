# Security Policy

## Scope

This repository is documentation (with templates/scripts introduced in a
later chapter). It does not run as a service and does not process user data,
so most classes of vulnerability that apply to applications don't apply
here. This policy still exists because:

- Templates and scripts published here (once added) may be copied into other
  repositories, so a flaw in them can propagate.
- Documentation can itself be a vector — e.g. a Git workflow or CI/CD
  recommendation that is insecure if followed literally.

Detailed security standards for repositories that *do* handle code,
infrastructure, and data are defined in
[`docs/10-security/`](docs/10-security/).

## Reporting a Vulnerability

If you find a security issue in this repository — an insecure recommendation,
a flawed template/script, or a leaked credential:

Please report security vulnerabilities through GitHub Private Vulnerability
Reporting. Do not open a public issue for security-sensitive reports.

Please include:

- A description of the issue and where it lives (file/path/line)
- Why it's a security concern (impact, who is affected)
- A suggested fix, if you have one

## Response

This is a personal, actively maintained project. Reports are reviewed as
soon as reasonably possible; there is no formal SLA. Fixes are released as
a normal commit/PR with a note in the relevant chapter once merged.

## Supported Versions

This repository does not use semantic versioning yet — it tracks a single
`main` branch. Once the [release process](docs/07-release-process/) chapter
is written and tagged releases begin, this section will be updated to
reflect which versions receive security fixes.
