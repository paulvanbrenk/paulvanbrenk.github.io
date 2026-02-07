---
layout: post
title: "Building an MCP Server with a Team of AI Agents"
date: 2026-02-07 10:00:00 -0500
categories: technology
---

I spent an evening building [typescript-mcp][repo], a Go server that gives
AI coding agents access to real TypeScript type checking. The interesting
part wasn't just the result. It was the process: I used a team of AI agents,
each with a distinct role, to design and build the whole thing. And I wrote
it in Go, a language I have very little experience with.

## The Problem

AI coding agents are surprisingly good at writing TypeScript. They're less
good at knowing whether what they wrote actually type-checks. They rely on
pattern matching and heuristics. They don't run the compiler. When the
codebase gets large enough, that gap starts to show.

Microsoft has been working on [tsgo][tsgo], a native Go port of the
TypeScript compiler, for almost a year now. It's still in preview, but it
already exposes an LSP server. I wanted to build a bridge: an
[MCP server][mcp] that sits between a coding agent and tsgo, translating
agent requests into LSP calls and returning clean, structured results.

## The Team

Multi-agent setups have gotten easy enough to be practical. Instead of
working with a single AI agent, you can define multiple [agent teams][teams]
with distinct roles and let them collaborate. That's what inspired this
approach.

I set up a team with specialized roles. The leadership group handled the
design:

- **Team Lead**: Coordinated the work, kept the project on track, and
  decided when to move between design and implementation phases.
- **Architect**: Proposed the three-layer architecture and made decisions
  about module boundaries, dependency flow, and protocol choices.
- **Devil's Advocate**: Challenged assumptions and poked holes in the
  design. Pushed back on complexity and asked "do we actually need this?"
- **User Representative**: Kept the focus on what an AI coding agent
  actually needs. Cut features that sounded nice but wouldn't matter in
  practice.

Then the implementation group built it:

- **Engineers**: Wrote the Go code. Multiple agents worked on different
  packages in parallel: the LSP client, the document sync layer, and the
  tool handlers.
- **Test Writers**: Wrote unit and integration tests alongside the
  implementation code.
- **Code Reviewer**: Reviewed every piece of code before it was accepted.
  This one was deliberately cranky. It pushed back on naming, error handling,
  unnecessary abstractions, and anything that felt over-engineered.

## How the Team Worked Together

The design phase came first. The architect proposed the overall structure.
The devil's advocate challenged it. The user representative anchored
decisions in real agent workflows. The team lead made final calls when there
was disagreement.

Once the design was settled, the engineers and test writers got to work.
The code reviewer sat at the end of each cycle and flagged problems. This
created a natural rhythm: build, review, fix, move on.

What surprised me was how well the role separation worked. The devil's
advocate caught several cases where the architect was over-designing. The
user representative killed a feature that would have added complexity
without helping agents in practice. The cranky reviewer caught inconsistent
error handling and naming issues that would have been easy to miss.

The role separation made it feel like coordinating a real team.

## The Architecture

The final design is a three-layer stack:

```
Coding Agent (Claude Code, etc.)
     |  MCP (stdio)
typescript-mcp (Go)
     |  LSP JSON-RPC (stdio)
tsgo (TypeScript compiler, native Go)
```

The MCP server spawns tsgo as a child process and communicates with it over
stdio using the LSP protocol. It exposes seven tools to the agent:
diagnostics, go-to-definition, hover (type info), find references,
document symbols, project info, and rename.

Each tool follows the same pattern: validate parameters, sync the file
with the LSP server, make the LSP call, and format the response into
something an agent can use without parsing LSP protocol details.

The most complex tool is `ts_rename`. It renames a symbol across the entire
project atomically, with rollback if anything fails. That one took the most
review cycles.

## Writing Go Without Knowing Go

I chose Go because tsgo is written in Go. Using the same language meant I
could lean on `go.lsp.dev` for mature LSP protocol libraries.

The catch: I have very little Go experience. I've read Go code before. I've
never built anything substantial in it.

This turned out to be a good test of the multi-agent approach. The engineers
wrote idiomatic Go. The code reviewer caught places where the code was doing
things in a non-Go way. I could focus on what I wanted the system to do
rather than fighting with syntax and conventions I don't know well.

I still had to review everything. I still had to understand the code well
enough to accept it. But the barrier to working in an unfamiliar language
was much lower than it would have been working alone.

There's a trade-off here. I now have a project in a language I'm not fluent
in. Maintaining it means either getting better at Go or continuing to rely
on agents for changes. For a personal project that's fine. For production
code at work, I'd be more cautious.

## What I Learned

**Role separation matters.** Giving agents distinct roles produced better
results than asking one agent to do everything. The design was more
considered. The code was more consistent. The tests were more thorough.

**The cranky reviewer is the most valuable role.** Left to their own
devices, the engineer agents would occasionally over-build. The reviewer
kept things simple. Every team needs someone who says "no" more often than
"yes".

**Unfamiliar languages are less scary with a team.** I would not have
attempted a Go project this size on my own in an evening. The agents handled
the language-specific details. I handled the architecture and decisions.

**You still own the result.** Same as my [earlier post on using LLMs for
coding][llm-post]. I reviewed every file. I tested the tools manually. The
agents wrote the code, but I'm responsible for what shipped.

## Closing Thoughts

Building typescript-mcp was a good experiment in using AI agents as a team
rather than a single tool. The role separation created useful tension:
engineers want to build, reviewers want to simplify, advocates want to
challenge. That tension produces better software.

The [project is on GitHub][repo] if you want to try it. It's early, but it
works.

[repo]: https://github.com/paulvanbrenk/typescript-mcp
[tsgo]: https://github.com/microsoft/typescript-go
[mcp]: https://modelcontextprotocol.io
[teams]: https://code.claude.com/docs/en/agent-teams
[llm-post]: /technology/2025/11/21/using-llms-for-coding.html
