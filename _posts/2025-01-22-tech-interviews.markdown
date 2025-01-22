---
layout: post
title: "Tech Interviews"
date: 2025-01-22 10:00:00 -0500
categories: technology
---

If you've looked at LinkedIn in the past couple of months (or years), you will
have seen posts from people about tech interviews. This is my contribution to
the discussion. I'll start with an overview of the state of interviewing for
software engineering roles and finish with a proposal for a better process. A
process that I think gives more insight into how candidates actually solve
problems and takes less time for both the candidate and the interviewer.

My recent experience is with senior-level interviews, so that's what I'm going
to focus on here.

## State of the Industry

Most tech interviews follow a very similar pattern, modeled after how Google,
Meta, Amazon, and other big-tech firms conduct interviews. They include one or
more of the following, totaling 5-7 rounds:

**Recruiter Screen**: A short call with a recruiter to discuss your experience,
the role, compensation, and next steps in the process.

**Hiring Manager Screen**: A longer call, similar to the recruiter call but goes
deeper into technical experience and covers some cultural and leadership
questions.

**Take-home Assignment**: These come in two flavors:

- A timed assignment with one or more tasks covering e.g. basic React or data
  structures/algorithms.

- A more open-ended project that gives you flexibility to implement it in your
  preferred technology.

**Tech-Screen**: Similar to the timed assignment but timeboxed to an hour. The
interviewer observes and answers questions.

**System Design**: You are asked to design the architecture for a well-known
system, like Uber or YouTube. This interview mainly decides if your experience
matches the job's level.

**Culture Fit / Leadership Principles**: A discussion of your previous
experience to see if you're a cultural fit and how you handle common challenges
like disagreements, scope creep, and missed schedules.

**Checking References**: Not technically an interview round, but something I've
seen more frequently.

Some of these rounds add more value than others. The recruiter and hiring
manager screens, along with the culture fit interviews, help determine if the
candidate will be a good addition to the team and company.

### Coding Questions

The coding rounds, on the other hand, add less value. They mostly test how well
a candidate can memorize and repeat common questions. There is a whole industry
of books, websites, and courses dedicated to this. This requires a lot of
preparation time, which disadvantages people who don't have that time due to
responsibilities like caring for children or family members, or having a busy
job.

Besides the time required to prepare, the coding questions don't actually test
how a candidate works day-to-day. I use Google, MDN, and the React docs daily to
remind myself of various APIs, not to mention modern AI tools like Copilot. Most
work doesn't involve algorithms to reverse linked lists, flip trees, or find the
shortest path.

### System Design

While system design is more useful than coding questions or a pop-quiz about a
random API in a popular framework, it is still flawed. It requires the candidate
to quickly come up with trade-offs between various solutions for a product
they've had only a few minutes to think about. Similar to the coding questions,
this again depends on how much time the candidate has been able to study common
system design questions.

### Checking References

A note about checking references: I can see why you'd want to talk to people a
candidate has worked with, but this puts them in a weird position. They have to
ask a huge favor from (former) co-workers without knowing if the company they're
interviewing with will respect their time. Moreover, the candidate has to
disclose their interviewing to their coworker. If they only give former
co-workers as references, the question is how relevant those references are if
they left that job two, three, or more years ago.

## A Better Process?

I don't think there is a single process that will work for every team or
company, but I think there can be several improvements that make the process
feel less random, less time-consuming, and more focused on real-world
experience.

The recruiter and hiring manager screens, as well as the culture/leadership
rounds, add a lot of value. When done by a well-prepared interviewer, these can
give a good indication of whether the candidate is a good match for the company
and team.

For the coding round, I would have the candidate spend three hours building a
project that highlights their skills. Either something they're passionate about
or a pre-scribed project. Something slightly more complex than a to-do app, but
not so complex that they need to spend an entire weekend on it. Next, I would
spend 45 minutes discussing their implementation and the choices they made. This
gives the candidate more flexibility in how and when they want to work on the
project and doesn't require them to take time off work. It also provides
something concrete to discuss, instead of a hypothetical product.
