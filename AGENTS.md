# Agent Notes (paulvanbrenk.github.io)

## Writing Voice

- Write in first person, pragmatic and calm; avoid hype/marketing tone.
- Prefer short paragraphs and plain language; define terms briefly when needed.
- Start with a quick framing paragraph (what this post covers and why).
- Use concrete examples, trade-offs, and clear takeaways; end with a short closing.

## Structure & Markdown

- Use `##` (and occasionally `###`) headings in Title Case to chunk ideas.
- Use numbered lists for step-by-step instructions; bullets for collections.
- When describing concepts/rounds, the `**Label**:` pattern fits well.
- Use blockquotes for external quotes and link to sources with descriptive text.
- Wrap lines at ~80 characters to match existing `_posts` formatting.

## Jekyll Post Conventions

- Add posts under `_posts/YYYY-MM-DD-kebab-case.markdown`.
- Use front matter like:
  - `layout: post`
  - `title: "..."` (quoted)
  - `date: YYYY-MM-DD 10:00:00 -0500` (include timezone)
  - `categories: technology|cat|...`

## Images & Code

- Put images in `assets/images/` and reference them via `/assets/images/...`.
- Always include descriptive alt text for images.
- Use fenced code blocks with a language tag (e.g. `yaml`, `js`).
- Use backticks for inline code, commands, and file paths.
