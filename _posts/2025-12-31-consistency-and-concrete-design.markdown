---
layout: post
title: "Consistency and Concrete Design"
date: 2025-12-31 10:00:00 -0500
categories: technology
---

Large codebases reward different instincts than small ones. Sean Goedecke’s
posts capture that shift: ship safely by following the grain of the system, and
design by working with the concrete details, not abstract principles. Here’s the
version of that philosophy I want to keep in front of me.

The originals are:

- [Mistakes engineers make in large established codebases][sg1]
- [You can't design software you don't work on][sg2]

## The Shared Thread

Both posts push against the same instinct: "I can reason this out from first
principles and then apply it to the codebase." In small projects that works. In
mature systems, the concrete details (and the accumulated weird edge cases)
dominate.

That leads to two related conclusions:

- If you want to change an established codebase safely, you need consistency.
- If you want to improve an established codebase, your "design" has to be
  grounded in how the system actually works today.

## Consistency Beats Clean Islands

In [Mistakes engineers make in large established codebases][sg1], Sean calls out
a "cardinal mistake": implementing a feature in the most reasonable way, while
touching as little legacy code as possible.

I've done this. It feels responsible: keep the blast radius small, keep the new
code "nice", avoid the messy parts. The problem is that in large systems, the
mess often encodes years of learned constraints.

**Consistency**: The goal is to make your change look like it belongs. That
usually means finding prior art and following it, even when it's awkward.

**Why it matters**: The existing patterns are often the safe path through
unknown complexity (odd user types, operational tooling, exceptions for specific
customers, historical data states, and so on).

**Long-term payoff**: Consistency is what makes broad improvements possible. If
every endpoint does auth differently, you can't fix auth "once". You have to fix
it everywhere, which usually means it never gets fixed.

## Design Conversations Should Be Concrete

In [You can't design software you don't work on][sg2], Sean argues that only
engineers who actively work in a system can do useful design for it, because
real design discussions are about concrete details, not generic principles.

> Only the engineers who work on a large software system can meaningfully
> participate in the design process.
>
> -- Sean Goedecke, [You can't design software you don't work on][sg2]

He draws a distinction that matches my experience:

**Generic design**: advice that applies when you understand the problem but not
the codebase. It can be helpful for greenfield systems, where there are few
constraints.

**Concrete design**: the day-to-day design work inside an existing system. It's
usually a small group of engineers talking about specific flows, files, and
trade-offs that only make sense if you know the system.

This also explains why "architecture" can go wrong when it becomes a separate
activity done far away from implementation. Without contact with the codebase,
it's easy to propose changes that are theoretically neat and practically
unshippable.

## How I (Want To) Work In Large Codebases

These are the practices I want to be more deliberate about when I'm working in
large codebases.

1. Start every change by finding prior art in the repo.
2. Prefer existing helpers and patterns over "better" bespoke code.
3. Assume I can't test every state combination; plan for monitoring and slow
   rollouts instead.
4. Be reluctant to add dependencies, because the maintenance cost will likely
   outlive my time on the team.
5. Keep PRs small, and get domain experts to review the riskiest touch points
   early. (And use a stacking system, like e.g [Graphite][sg3]).
6. Treat design docs as concrete maps: link to the code, name the trade-offs,
   and describe the migration path.

## Ship First, Improve Next

Consistency can preserve bad patterns. But inconsistency makes it hard to change
anything at scale. The move I like is:

- Follow the existing path to ship safely.
- Then, if the pattern is truly harmful, improve it in a way that brings the
  rest of the codebase along (shared helpers, migrations, lint rules, paved
  paths, whatever fits).

That's slower than building a clean island. It's also the only approach I've
seen that compounds over time.

## Closing Thoughts

In big systems, consistency keeps you safe and concreteness keeps you honest.
That’s the work.

[sg1]: https://www.seangoedecke.com/large-established-codebases/
[sg2]: https://www.seangoedecke.com/you-cant-design-software-you-dont-work-on/
[sg3]: https://www.graphite.com/
