# attune-docs

**Context-sensitive help for your AI product's users.**

Ship help content the same way you ship code — authored in
templates, version-controlled, and delivered at the exact moment
your users need it.

attune-docs is a two-plugin help platform for Claude Code
(with Gemini and other platform adapters planned):

- **attune-help** — lightweight runtime reader. Reads `.help/`
  templates with progressive depth
  (concept → task → reference). No AI keys required. Install
  this alone when you just want to consume help content someone
  else wrote.
- **attune-author** — AI-powered authoring companion.
  Generates, maintains, and validates `.help/` templates via a
  staleness-aware workflow. Install this alongside attune-help
  when you are the one building the help content.

## Quick start

### I want to read help templates

```bash
claude plugin marketplace add Smart-AI-Memory/attune-docs
claude plugin install attune-help@attune-docs
```

### I want to author and ship help content

```bash
claude plugin marketplace add Smart-AI-Memory/attune-docs
claude plugin install attune-help@attune-docs
claude plugin install attune-author@attune-docs
```

## Why "docs"?

"Docs" is the category people actually search for. But this is
not a static site generator or a wiki — it is a runtime,
context-sensitive help system your AI product uses to answer
user questions at the exact moment they need the answer.
Authored like docs, delivered like chat.

## Ecosystem

| Plugin | Install alone | Install together |
|--------|---------------|------------------|
| attune-help | Read-only: consume `.help/` templates shipped by someone else. No AI keys needed. | Read and author templates in the same project. |
| attune-author | Does not install alone — depends on attune-help at runtime. | Generate, maintain, and validate `.help/` templates. |

Looking for developer workflows (security audits, code review,
test generation) instead of a help platform? See
[Smart-AI-Memory/attune-ai](https://github.com/Smart-AI-Memory/attune-ai).

## How updates work

This marketplace pins to specific tags on `Smart-AI-Memory/attune-ai`
via `git-subdir` sources. When a new version of attune-help or
attune-author ships, update with:

```bash
/plugin marketplace update attune-docs
/plugin install attune-help@attune-docs
```

(Both commands are required — the first refreshes the manifest,
the second upgrades the installed plugin.)

## License

Apache 2.0. See [LICENSE](LICENSE).
