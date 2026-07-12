# Engineering Principles

Ten positions that hold across every project in this ecosystem. Each one
names a trade-off, not just a preference — the practical consequence is
what makes it checkable against an actual decision rather than agreeable in
the abstract.

### Solve Real Problems

**Statement:** A project exists because a real, observed problem needs
solving, not because a technology is interesting to try.

Here, a real problem means a named person or project has already hit the
limitation, has a current workaround, and would be better served if that
workaround disappeared.

**Why it matters:** A problem chosen for the interest of the technology
behind it, rather than for the need behind it, produces software that costs
the same to build, document, and eventually maintain as software people
actually use — without the return. The technology being interesting is not
evidence that anyone has the problem it's being used to solve.

**Practical consequence:** Before starting a project, write down who has
the problem and what they currently do instead. If the honest answer is
"no one, hypothetically," it stays a local experiment, not a repository.

### Automate What Repeats

**Statement:** A task performed by hand more than a few times in
comparable form is a candidate for automation, not a routine to keep.

**Why it matters:** Manual repetition hides its own cost because each
instance feels small on its own; the cost that automation buys back is the
sum of all of them plus the inconsistency between repetitions. Automation
is not free either — it has to be written, tested, and kept working — so it
is only a win once the manual cost it replaces is larger than that.

**Practical consequence:** Automate a task once it has been done three
times in a comparable way; before that, do it by hand and note what
varies between instances.

### Reliability Over Novelty

**Statement:** When an established approach and a newer one both solve the
problem, the established one wins unless the newer one removes a specific,
demonstrated constraint.

**Why it matters:** Novelty carries a real cost: less accumulated knowledge
to draw on when it breaks, fewer edge cases already found by others, and a
higher chance the tool itself is still changing underneath the project. That
cost is worth paying when it buys back something the established approach
genuinely can't provide — not because the newer approach is more current.

**Practical consequence:** A new dependency, language, or pattern is
adopted only with a written statement of the specific constraint it
removes, checked against what adopting it costs.

### Explicit Systems Over Hidden Assumptions

**Statement:** Behavior that depends on an assumption written down nowhere
is a defect, even while it happens to work.

**Why it matters:** Hidden assumptions — implicit ordering, an
undocumented environment variable, a value that "just happens" to be true
right now — survive only as long as the conditions that created them, and
by the time those conditions change, the person debugging the failure is
rarely the person who made the assumption. Writing the assumption down does
not remove the risk; it turns an invisible failure into a reviewable one.

**Practical consequence:** Any behavior that depends on an assumption gets
a comment, a configuration value, or an explicit check — never silence.

### Infrastructure Should Fail Loudly

**Statement:** A failure that is silently absorbed is worse than one that
stops the system, because it postpones the cost and hides where it landed.

**Why it matters:** A swallowed exception, a retry that never surfaces, or
a fallback that quietly serves stale data trades an immediate, diagnosable
problem for a deferred one with no evidence left by the time it's noticed.
The system still failed either way — the only choice is whether that
failure is visible while it can still be traced back to its cause.

**Practical consequence:** Errors are logged with enough context to act on
and are never caught only to be discarded; any fallback path records that
it was used, somewhere visible.

### Documentation Is Part Of The Product

**Statement:** Software without a stated purpose, a way to run it, and a
reason it exists is incomplete, regardless of how well the code works.

**Why it matters:** Code communicates how something works; it rarely
communicates why it exists or why it was built this way, and that reasoning
is what a future maintainer — including the original author, later — needs
to change it safely. Treating documentation as something added after the
code is finished guarantees it lags behind the code and eventually
contradicts it.

**Practical consequence:** A repository without a README stating its
purpose and how to run it does not get published, regardless of whether the
code works.

### Dependencies Create Operational Responsibility

**Statement:** Adding a dependency is agreeing to track its
vulnerabilities, its breaking changes, and its eventual abandonment for as
long as the project runs, not just importing code that currently works.

**Why it matters:** The cost of a dependency is not paid once at install
time; it recurs as advisories to check, updates to review, and the risk
that its maintainer disappears and leaves it frozen. A dependency that
saves an afternoon of work today can cost more than that afternoon,
repeatedly, over the life of the project.

**Practical consequence:** A dependency is added only when it is
justifiable against writing the equivalent code directly; one with a single
maintainer or no recent activity gets a written note on why the risk is
accepted anyway.

### Maintenance Is Part Of Shipping

**Statement:** A release is not finished at the moment it ships — it is
finished when someone has committed to keeping it working.

**Why it matters:** Treating shipping and maintaining as separate phases
lets unmaintained software accumulate under the appearance of being done,
which is worse for anyone building on it than if it had never shipped,
because they now depend on something that quietly stopped being supported.
The maintenance commitment is a cost that has to be accounted for before
the release, not discovered afterward.

**Practical consequence:** Before a first release, who fixes what, and for
how long, is decided — not assumed by default.

### Security And Privacy Are Design Inputs

**Statement:** Security and privacy decisions are made when a system is
designed, accepting earlier constraints on data and access instead of a
larger retrofit later.

**Why it matters:** Retrofitting security onto a system not designed with
it constrains the fix to whatever the existing architecture allows, which
is usually worse than the choice that would have been made up front. The
same applies to privacy — what data a system collects and where it lives is
far easier to constrain before storage and access patterns already exist.

**Practical consequence:** Any system handling credentials, personal data,
or user input must state, before it is built, what it stores, who can
access it, and what happens if that access is compromised.

### Do Not Publish Software You Are Unwilling To Maintain

**Statement:** Publishing a repository under this name is an implicit
statement that it will get at least a minimal, ongoing response to real
issues; if that isn't true, it should not be published as if it were.

**Why it matters:** An abandoned public repository still costs its users —
issues go unanswered, an API is never fixed, and the abandonment attaches
to the author's name, not just the project's. An unpublished experiment
carries none of that cost; a published one does, whether or not that was
the intent.

**Practical consequence:** Before publishing, the project is labeled
explicitly as maintained or archived-on-arrival — it is never left to be
assumed one or the other.
