---
layout: post
title: "From One to Ten Is the Hard Part"
date: 2026-05-04 10:00:00 -0500
categories: technology
---

A lot has been written about 0-to-1: how to find an idea, scope an MVP,
get the first prototype in front of users. With coding agents now able to
turn a rough product brief into a working application in a weekend, that
phase has lost most of its mystique. Building the thing is no longer the
bottleneck. Getting it used is.

I have [written before][prior] about why engineering is not what kills early
products. This post is about what does. Going from 1 to 10, from a working
MVP to a company that actually makes money, is mostly a distribution and
retention problem. That is a different game than the one most
engineering-led teams know how to play.

## Distribution Is the Real Moat

If more teams can build a usable version in a weekend, then having built
it stops being much of a competitive advantage. The advantage shifts to
whether you can reach the people who would benefit from it. That work is
unglamorous and mostly invisible to engineers.

Distribution is a portfolio problem, not a single channel. The teams I
watch succeed pick two or three channels and get genuinely good at them
before adding a fourth. SEO, partnerships, a specific community, paid
acquisition with a clear payback window, founder-led sales, content that
actually ranks. None of these are quick. All of them compound.

The trap is treating distribution as a thing you bolt on after the
product is "ready." It never is, and the bolt-on never works. If you
have not figured out how a stranger finds you by month three, the
product is not the problem.

## Retention Is the Number That Matters

You can buy acquisition. You cannot buy retention. Retention is the
single number that tells you whether you have a real product or just a
demo people tried once.

The shape of the curve matters more than the average. A flat tail of
users who keep coming back week after week is a business. A steep
decline that never flattens is a leaky bucket, and pouring more
acquisition into it just makes you run out of money faster.

Two practices make retention legible:

**Charge money early**: not because you need the revenue, but because
nothing clarifies a value proposition like asking someone to pay for it.
A free user who churns gives you a weak signal. A paying user who churns
usually tells you where the value proposition broke down.

**Define the "habit moment"**: the specific action that, if a user takes
it in their first session, predicts they will still be around a month
later. For most products this is one or two events, not a feature list.
Find it, then organize onboarding around getting people to it.

If you do not know your week-four retention number, you are still
guessing about whether you have a company yet.

## The First Five Minutes Decide Everything

Most products lose their users in the first session. Not because the
product is bad, but because the path from signup to value is too long,
too unclear, or asks for too much before giving anything back.

This is where engineers consistently underinvest. The features built in
month two get more attention than the empty state, the welcome email,
the third screen of onboarding, the moment when the user has to decide
whether this is worth another five minutes.

The teams that cross from 1 to 10 treat the first session as the most
important surface area in the product. They watch session recordings.
They count how many new users hit the habit moment, and they treat
anything blocking that as a top-priority bug, even if technically it is
working as designed.

A faster path to the first useful outcome will outperform almost any
feature you could ship that week.

## Talking to Users Is the Job

Between 1 and 10, talking to users is not a research activity. It is the
job. Not formal interviews on a quarterly cadence, but short, frequent
conversations: support tickets answered personally, churned users asked
why, paying users asked what almost stopped them.

Support is the highest-signal data source most teams ignore. Every
ticket is a user telling you exactly where the product failed them, in
their own words, with the context of what they were trying to do. If
the founder or the PM is not reading every ticket for longer than feels
reasonable, the team is flying blind.

The output of this is rarely a feature request. It is usually a small
change to copy, a reordering of steps, a default that should have been
flipped, a price that needs to move. None of it is exciting work. All
of it compounds.

## Engineering in Service of the Loop

Engineering still matters here, but its job changes. The work that moves
the needle between 1 and 10 is the work that shortens the loop between a
user signal and a product change.

Concretely: instrumentation good enough that you can answer a retention
question without writing a one-off script. Feature flags so changes can
ship and revert without ceremony. A deploy pipeline fast enough that a
fix lands the same day the support ticket arrives. Pricing and plan
changes that do not require an engineer.

If you find yourself debating whether to rewrite the service layer or
adopt a new ORM, that is usually a sign you have lost the plot. The
question to keep asking is: what is the smallest change that would make
one more user stay this week, and can the team answer that question
without me?

## Closing Thoughts

Zero to one used to separate the people who could ship from the people
who only talked about shipping. That distinction is fading. The bar to
shipping is much lower now.

One to ten separates products from companies. It is mostly not an
engineering problem. It is a distribution problem and a retention
problem, with engineering playing a supporting role in the feedback
loop. The team that wins is not the one with the cleanest codebase. It
is the one that figured out how to bring users in and give them a reason
to stay.

[prior]: /technology/2025/11/07/startup-lessons.html
