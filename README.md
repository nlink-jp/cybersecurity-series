# cybersecurity-series

A collection of CLI tools for cybersecurity workflows, maintained under the [nlink-jp](https://github.com/nlink-jp) organisation.

Each tool is a standalone project with its own repository, release cycle, and documentation.
This umbrella repository tracks them together as git submodules and hosts shared conventions.

## Tools

| Tool | Description |
|------|-------------|
| [ioc-collector](https://github.com/nlink-jp/ioc-collector) | Autonomously researches security incidents from URLs, CVE IDs, or natural language — extracts IoCs into Markdown reports and STIX 2.1 bundles |
| [product-research](https://github.com/nlink-jp/product-research) | Researches products and services on the web — outputs ToS, privacy, and data security analysis as structured reports |
| [ai-ir](https://github.com/nlink-jp/ai-ir) | AI-powered incident response analysis — analyzes Slack IR conversation exports to generate summaries, activity reports, role inference, and reusable investigation tactics |
| [news-collector](https://github.com/nlink-jp/news-collector) | News collection agent — collects, structures, tags, and summarizes news articles via Gemini for daily intelligence gathering |

## Design Philosophy

- **AI-augmented**: Tools use LLMs (Gemini, Claude, OpenAI-compatible endpoints) as the intelligence layer for research and analysis tasks.
- **Structured output**: All tools produce machine-readable JSON alongside human-readable Markdown — suitable for downstream automation.
- **Security-first**: IoC defanging, prompt injection defense, and no-exfiltration-by-default are built-in design constraints.
- **Pipe-friendly**: Tools read from files or stdin and write to files or stdout; composable with `jq` and each other.

## Runtime

All tools are Python projects managed with [uv](https://docs.astral.sh/uv/). Install dependencies with:

```sh
uv sync
```

Run tools with:

```sh
uv run <tool-entrypoint> [args]
```

## Shared Conventions

See [CONVENTIONS.md](https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md) for coding, documentation, and release standards that apply across all tools in this series.
