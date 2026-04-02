---
layout: post
title: "A Product Cadence That Works for Us"
date: 2026-04-01 10:00:00 -0500
categories: technology
---

My team ships a web application continuously. We do not do sprints. We do
not have a build/stabilize/release cycle. Code goes out when it is ready,
and we can revert it quickly if something goes wrong. That changes how we
plan, communicate, and iterate, and I think the result is better than the
sprint model we used before.

This is what works for us. It might not work for you. Take what sounds
right and leave the rest.

## Weekly Planning, Not Sprint Planning

Every Monday, the Product Manager (PM) meets with our founder and a subject
matter expert. The goal is to figure out what the focus of the week should
be. This is not a formal planning ceremony. It is a short conversation
about what matters most right now.

On Tuesday morning, the PM and tech leads meet to talk through the work.
We figure out who makes the most sense to pick things up, or whether
someone should
keep going on what they already started. There is no pressure to shuffle
work around just because a new week started. Continuity matters.

New tasks go into triage. The PM moves them to the backlog with appropriate
priority. That is the whole intake process.

## The PM Is Part of the Team

This is worth calling out because I have seen the alternative. Our PM is
not someone who shows up for planning and then disappears. They are in our
standups. They are in our retros. They have context on what is in progress,
what is blocked, and what just shipped. That means fewer handoffs, fewer
misunderstandings, and faster decisions about scope and priority.

## Standups and Retros

We do standup three times a week. Before each standup, every team member
writes a note in a shared document covering what they worked on and what
they are working on next. This keeps the actual standup short and focused.
If someone is blocked, we usually know before the meeting starts.

We do a retro once a week. Our manager is not in the room, and we do not
have a transcriber. That is deliberate. It gives people more freedom to
say what they actually think. Anything actionable gets communicated up
anonymously by the tech lead and PM. This keeps the retro honest without
making anyone feel exposed.

## Continuous Shipping Changes How You Iterate

Because we ship continuously, we do not batch changes into releases. A new
feature goes out behind a feature flag. An incremental improvement goes out
to everyone. If something breaks, we revert it. The blast radius of any
single change stays small.

This also changes how we think about iteration. With AI agents helping
with a lot of the first-draft code, the cost of trying an approach is
lower than it used to be. Where we used to get one pass at a feature
before it had to ship, we now get three or four iterations in the same
window. Engineers can try different approaches, throw away what does
not feel right, and converge on a UX that actually works before
marking the task as ready for review.

That does not mean we skip review. It means the thing that lands in review
has already been through several rounds of refinement. The conversation
shifts from "does this work" to "is this the right experience."

## Communication and Trust

None of this works without quick communication and a baseline of trust
between people on the team. Lightweight planning only stays lightweight
if questions get answered quickly and people feel comfortable raising
concerns early.

For us, that means being in the office. When I need to talk through a
tradeoff with the PM or check an assumption with another engineer, I walk
over. There is no scheduling overhead, no waiting for someone to see a
message. The turnaround on small decisions is minutes, not hours.

That does not mean this requires an office. It means it requires whatever
gives your team fast, low-friction communication and enough mutual trust
that people flag problems instead of hiding them. If your team gets that
from being remote with strong async habits, that works too. The mechanism
matters less than the result.

## What We Traded Away

We do very little upfront design, both UX and technical design. That is
a conscious tradeoff. For a continuously shipped web application,
putting a real feature in front of users reveals what works and what
does not much faster than a design document or architecture diagram.
The feedback loop is tighter, and we trust it more.

But this only works because we invested in automated guardrails.
Linters, the compiler, unit tests, automated review tools that flag
suspicious changes, and other early warning systems catch the obvious
failures before they reach users. Without those, shipping fast would
just mean breaking things fast. The safety net is what makes the speed
sustainable.

## What I Would Tell Another Team

Do not copy this process. Look at what problems you are actually having and
see if any of these ideas help. If your sprints feel like overhead, maybe
you do not need them. If your PM is disconnected from the team, maybe they
should be in standup. If your retros feel performative, maybe the wrong
people are in the room.

The thing that holds this together for us is not any single practice. It is
that we ship continuously, revert quickly, and keep planning lightweight.
Everything else follows from that.

That fits our product and our team. The useful part is not the exact
process. It is being honest about what your release model allows, and
then building a cadence that matches it.
