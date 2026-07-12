# Decision Framework

This applies the [engineering principles](engineering-principles.md) to six
recurring categories of decision. Each category lists what to ask, what
evidence answering it requires, when to reject the decision outright, and
what a good outcome looks like. A compact checklist at the end condenses all
six into a pre-implementation gate.

## New Project Ideas

**Questions:** Who has this problem, specifically, right now? What do they
currently do instead? Does an existing project — mine or someone else's —
already solve it well enough? What is the smallest version that tests
whether the problem is real?

**Evidence required:** A concrete instance of the problem occurring, not a
hypothetical one. A record of what was checked for existing solutions and
why they don't work.

**Rejection criteria:** The problem is inferred from a trend or a
technology rather than an observed need. An existing project already solves
it and the gap is cosmetic. The idea can't be described without referencing
the technology used to build it.

**Expected outcome:** A local, unpublished prototype that either confirms
the problem is real and worth a public repository, or is discarded without
becoming one.

## New Features

**Questions:** Who asked for this, or what usage pattern shows it's needed?
What does adding it cost in future maintenance, beyond the time to build
it? Does it fit the project's existing scope, or change it?

**Evidence required:** A specific use case, issue, or observed usage gap —
not a guess at what might be useful. An estimate of what the feature adds
to the maintenance surface: new configuration, new failure modes, new
dependencies.

**Rejection criteria:** The feature exists to make the project look more
capable rather than be more useful. It duplicates functionality better
served by composing with another tool. No one has asked for it and no
observed usage supports it.

**Expected outcome:** The feature is implemented with its maintenance cost
accepted explicitly, or the request is declined with the reason recorded.

## Dependencies

**Questions:** What does this remove that would otherwise have to be
written and maintained directly? Who maintains it, how actively, and what
happens if they stop? What is the blast radius if it has a vulnerability or
a breaking change?

**Evidence required:** Recent commit or release activity on the dependency.
Confirmation that the equivalent functionality is nontrivial to write
directly.

**Rejection criteria:** It replaces a small amount of straightforward code.
It has a single maintainer with no recent activity and no clear successor.
Its license or data-handling behavior is unclear.

**Expected outcome:** The dependency is added with a written reason, or the
equivalent functionality is written directly instead.

## Architectural Changes

**Questions:** What constraint does the current architecture impose that
this change removes? What does the change break, and what has to migrate?
Can the change be reversed if it turns out to be wrong?

**Evidence required:** A specific, currently occurring limitation caused by
the existing architecture. A migration plan for anything the change
affects.

**Rejection criteria:** The change is motivated by a newer pattern rather
than a removed constraint. It can't be reversed and its downside hasn't
been evaluated. It's proposed with no migration plan for existing users or
data.

**Expected outcome:** The change ships with its constraint and migration
path documented, recorded as an entry in [`12-adrs`](../12-adrs/).

## Open-Sourcing Software

**Questions:** Can someone who isn't me use this without asking me
questions? Am I willing to respond to issues and pull requests on it? Does
it need secrets, internal references, or unfinished pieces removed before
publishing?

**Evidence required:** Documentation sufficient for an outside user to run
it unassisted. A completed review for credentials, internal references, and
unfinished pieces.

**Rejection criteria:** It only works with undocumented local configuration
or context. It's being published to show progress rather than because it's
usable. No time is available to respond to issues for the foreseeable
future.

**Expected outcome:** The repository is published as either actively
maintained or explicitly archived-on-arrival — never left to be assumed as
maintained by default.

## Continuing, Deprecating, Archiving, Or Deleting A Project

**Questions:** Does this still solve the problem it was built for, for
anyone, including me? What does keeping it running currently cost — time,
dependencies, exposure? Is anyone depending on it who would be harmed by
its removal?

**Evidence required:** Recent evidence of actual use — issues, downloads,
personal use — or the documented lack of it. The current maintenance cost,
even if the estimate is rough.

**Rejection criteria (for continuing as-is):** No evidence of use and no
personal need, but the cost of running it continues — security exposure,
dependency drift. The problem it solved no longer exists or is better
solved elsewhere.

**Expected outcome:** One explicit status is assigned: continued,
deprecated with a stated end date, archived and marked read-only, or
deleted — only once nothing depends on it.

## Decision Checklist

Before a decision is accepted, rejected, continued, stopped, published,
kept private, archived, or deleted:

- [ ] The need is observed, not inferred from a trend.
- [ ] No existing project — mine or external — already solves this
      adequately.
- [ ] Ownership is explicit: who is responsible if this breaks.
- [ ] The operational cost — dependencies, maintenance, security exposure —
      is stated, not assumed.
- [ ] There is a stated willingness to maintain this, or it is labeled
      otherwise: archived-on-arrival, experiment, deprecated.
- [ ] The output matches its label — an experiment is not published as a
      finished product, and a finished product is documented well enough to
      be used without me.
- [ ] The opposite decision has been considered explicitly: reject instead
      of accept, stop instead of continue, keep private instead of publish,
      or delete instead of archive.
- [ ] The result is one concrete action: implement, reject, prototype
      locally, publish, keep private, continue, deprecate, archive, or
      delete.
