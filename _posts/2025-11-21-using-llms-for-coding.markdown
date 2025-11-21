---
layout: post
title: "Using LLMs for Coding"
date: 2025-11-21 10:00:00 -0500
categories: technology
---

I've been using coding agents a lot this year, both in my job and for personal
projects. They are much more useful than I initially expected. I'm not going to
recommend a specific one, since the ones I used paid versions for (Claude, Amp
with Gemini, ChatGPT Code) all perform very similar.

Large language models are great for rapid prototyping. Especially when you work
with modern frameworks. I've used them with React, Tailwind, and .NET. They can
help you go from an idea to a working proof of concept in an evening.

You describe the feature you want. You paste in a bit of existing code. The
agent writes a first draft. It sets up components, routes, styles, and basic
data flow. The quality is not perfect. It's often good enough to react to and
improve.

## Where LLMs Work Well

I find coding agents very good at two things.

First, they help with scaffolding new code. A new React page. A Tailwind
layout. A .NET controller. They can wire these together fast. They also tend to
follow the common patterns in each ecosystem. That makes it easy to read and
maintain the result.

Second, they're good at finding things in an existing codebase. You can paste
in a file and ask where a certain value comes from. Or you can ask for every
place that calls a method. You can ask how a feature flows from the UI to the
database. This is often faster than manual grepping or clicking around.

## Fixing Complex Bugs

For complex bugs the picture is different. Coding agents can propose fixes. In
my experience they're less reliable here. Especially when the bug spans
multiple layers or services.

They work much better when you have a complete set of tests. Or at least good
coverage for the area you are changing. Then the agent can rely on failing
tests to guide it. Without tests the agent has to guess. It tends to produce
code that looks right. It compiles. It passes a quick skim. It still doesn't
fix the real problem.

## You Still Have to Review

Using a coding agent means you still have to think. You need to get good at
reviewing the code it writes. You should expect to dive in and manually fix
things.

More prompting does not always fix the code. At some point you stop asking the
agent to "try again". You take the best version it produced. Then you edit it
yourself. Rename things. Simplify logic. Add tests. Remove unused code. This is
often faster than trying to talk the agent into the exact change you want.

If you're not comfortable making these edits you should not ship the code. You
are still responsible for what ends up in your repo.

## Beware of Very New Tech

One more thing to keep in mind. Coding agents are trained over a period of time.
They are not updated with every new release blog post. They won't be familiar
with packages, frameworks, or features released in the past week. In
some cases even the past few months.

If you are working with a brand new library you should not depend on the agent
to know the right patterns. You may get made up APIs. Or old versions of the
docs. Or examples that do not compile. You still need to read the official
documentation and release notes yourself.

## Averages and Novel Ideas

LLMs work by learning patterns from large amounts of existing code. They're
very good at the average solution. The thing most people would do. This makes
them great for standard CRUD apps. It makes them less useful when you want a
novel approach.

If you want something unusual you often have to lead the agent. A good example
is the HTML `<dialog>` element and the Popover API. These are powerful tools
for building modern UI. You will not see them used as often in generated code.
Most training data still uses custom modal components and older patterns.

In those cases you bring the idea. You decide to use `<dialog>` or popovers.
The agent can still help with wiring and edge cases. But you provide the spark.

## Closing Thoughts

Coding agents are a great tool for rapid prototyping. They help you explore
ideas faster. They help you navigate large codebases. They are less good at
fixing deep bugs without strong tests. They lag behind very new technology.

Use them as an accelerator. Not as a replacement for your own judgment. You
still need to read the code. You still need to own the changes.
