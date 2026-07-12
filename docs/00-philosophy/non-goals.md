# Non-Goals

What this ecosystem deliberately does not optimize for, and what it
optimizes for instead. Stated explicitly so an absence — of a feature, a
release, a repository — isn't mistaken for an oversight.

### Repository Count

**Rejected because:** A large number of repositories isn't evidence of
engineering output; most of that count would be unfinished or unmaintained
experiments made public for the sake of visibility.

**Optimized for instead:** A small number of repositories that are
documented, working, and maintained.

### Stars And Followers As Primary Goals

**Rejected because:** Popularity metrics reward visibility and framing, not
correctness or usefulness, and optimizing for them shifts effort away from
the software itself.

**Optimized for instead:** Usefulness to whoever actually has the problem
the software solves, whether that's one person or many.

### Trend Chasing

**Rejected because:** Building around whatever is currently popular
produces software justified by timing rather than by a durable problem, and
it ages out as fast as the trend does.

**Optimized for instead:** Problems with observed users, current
workarounds, and durable constraints.

### Artificial Release Frequency

**Rejected because:** Releasing on a schedule regardless of whether there's
a meaningful change to ship produces noise, forces unfinished work out the
door, and trains users to stop reading release notes.

**Optimized for instead:** Releases that correspond to a real, documented
change, on whatever cadence that actually produces.

### Premature Abstraction

**Rejected because:** Generalizing code before there are at least two
concrete cases to generalize from produces an abstraction shaped by
guesswork, which is usually wrong and more expensive to unwind than the
duplication it replaced.

**Optimized for instead:** Concrete, duplicated code until a second real
case justifies the shared abstraction.

### Framework Loyalty

**Rejected because:** Choosing a tool because it was used before, rather
than because it fits the current problem, optimizes for familiarity over
fit and accumulates tools that no longer match what's being built.

**Optimized for instead:** Selecting the tool whose constraints, operating
cost, and failure modes fit the current project.

### Unnecessary Dependencies

**Rejected because:** Every dependency not clearly justified against the
cost of writing the equivalent code directly is operational weight taken on
for no corresponding benefit.

**Optimized for instead:** The smallest dependency set that still avoids
reimplementing genuinely nontrivial work.

### Publishing Unfinished Software

**Rejected because:** Publishing unfinished work optimizes for visibility
before the project has a stable usable shape.

**Optimized for instead:** Keeping unfinished work local, or labeling it
explicitly as an experiment.

### Supporting Every Possible Use Case

**Rejected because:** Accepting every use case a project could
theoretically support turns a focused tool into a general one that does its
original job worse and multiplies the surface area that has to be
maintained.

**Optimized for instead:** A clearly scoped set of use cases, with
unsupported cases stated explicitly rather than left ambiguous.

### Maintaining Projects Indefinitely Without Real Value

**Rejected because:** Keeping a project nominally alive after it stops
being used or needed consumes attention that could go to something that
still matters, and makes its support status unclear to users.

**Optimized for instead:** An explicit status for every project —
continued, deprecated, archived, or deleted — decided using the criteria in
[`decision-framework.md`](decision-framework.md).
