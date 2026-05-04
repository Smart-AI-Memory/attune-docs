# attune-docs

**Claude Code plugins for the attune documentation toolchain.**

Ship help content the same way you ship code — authored in
templates, version-controlled, and delivered at the exact moment
your users need it.

attune-docs hosts three Claude Code plugins covering the
author → reader → visualize loop:

- **attune-help** — lightweight runtime reader. Reads `.help/`
  templates with progressive depth
  (concept → task → reference). No AI keys required. Install
  this alone when you just want to consume help content someone
  else wrote.
- **attune-author** — AI-powered authoring companion.
  Generates, maintains, and validates `.help/` templates via a
  staleness-aware workflow. Install this alongside attune-help
  when you are the one building the help content.
- **attune-gui** — local dashboard for the whole stack. Health
  probes, template browser, spec authoring, RAG quality gates,
  jobs queue. Launches in the Cowork preview pane via
  `/attune-gui`.

The toolchain also includes [`attune-rag`](https://pypi.org/project/attune-rag/),
the Python retrieval library that powers grounded answers
(P@1 ≥ 73% on benchmarks). It's a library, not a Claude Code
plugin — install it via `pip` as a dependency of your tool.

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

### I want the local dashboard

```bash
claude plugin marketplace add Smart-AI-Memory/attune-docs
claude plugin install attune-gui@attune-docs
pip install attune-gui   # the Python sidecar the plugin launches
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
| attune-gui | Standalone local dashboard. Works against any attune workspace. | Visualize and operate the whole stack from one pane. |

| Library (PyPI) | Role |
|---|---|
| [`attune-rag`](https://pypi.org/project/attune-rag/) | Keyword + semantic retrieval. P@1 ≥ 73% on benchmarks. Used by attune-help for grounded retrieval. |

Looking for developer workflows (security audits, code review,
test generation) instead of a help platform? See
[Smart-AI-Memory/attune-ai](https://github.com/Smart-AI-Memory/attune-ai)
— the parent framework that built this toolchain.

## How updates work

When a new version of any plugin ships, update with:

```bash
/plugin marketplace update attune-docs
/plugin install attune-help@attune-docs    # or attune-author / attune-gui
```

(Both commands are required — the first refreshes the manifest,
the second upgrades the installed plugin.)

## License

Apache 2.0. See [LICENSE](LICENSE).
