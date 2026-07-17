# cybersecurity-series

A collection of CLI tools for cybersecurity workflows, maintained under the [nlink-jp](https://github.com/nlink-jp) organisation.

Each tool is a standalone project with its own repository, release cycle, and documentation.
This umbrella repository tracks them together as git submodules and hosts shared conventions.

## Tools

| Tool | Description |
|------|-------------|
| [abuse-lookup](https://github.com/nlink-jp/abuse-lookup) | Checks IP address reputation against the AbuseIPDB API — CLI + local MCP server with a TTL cache; the online, reputation-focused sibling of asn-lookup (Go) |
| [doh-lookup](https://github.com/nlink-jp/doh-lookup) | Collects a domain's DNS records over DoH (Cloudflare/Google) — queries out-of-band over HTTPS so investigative lookups stay distinguishable from ordinary DNS; forward profile + PTR reverse, states the resolver/endpoint and DNSSEC AD in every result; CLI + local MCP server, no credentials (Go) |
| [icloud-relay-lookup](https://github.com/nlink-jp/icloud-relay-lookup) | Reports whether an IP is an Apple iCloud Private Relay egress IP — offline lookup from a cached copy of Apple's egress-ip-ranges.csv, with geo hints; CLI + local MCP server, no credentials (Go) |
| [tor-exit-lookup](https://github.com/nlink-jp/tor-exit-lookup) | Reports whether an IP is a Tor Exit node — offline lookup from a cached copy of the Tor Project's torbulkexitlist; CLI + local MCP server, no credentials (Go) |
| [whois-lookup](https://github.com/nlink-jp/whois-lookup) | Looks up the registration data of a domain, IP, or AS number — RDAP-first with port 43 WHOIS fallback and in-house IDN punycode; CLI + local MCP server, no credentials (Go) |
| [ioc-collector](https://github.com/nlink-jp/ioc-collector) | Autonomously researches security incidents from URLs, CVE IDs, or natural language — extracts IoCs into Markdown reports and STIX 2.1 bundles |
| [product-research](https://github.com/nlink-jp/product-research) | Researches products and services on the web — outputs ToS, privacy, and data security analysis as structured reports |
| [cti-graph](https://github.com/nlink-jp/cti-graph) | Local-first threat intelligence attack graph analysis platform — SAGE-inspired, backed by local SQLite |
| [cti-primer](https://github.com/nlink-jp/cti-primer) | Generates CTI PIRs (Priority Intelligence Requirements) from business context — BEACON-inspired, runs on local LLMs or dictionary-only mode, no cloud services required |
| [ai-ir](https://github.com/nlink-jp/ai-ir) | AI-powered incident response analysis — analyzes Slack IR conversation exports to generate summaries, activity reports, role inference, and reusable investigation tactics |
| [ai-ir2](https://github.com/nlink-jp/ai-ir2) | Next-generation AI-powered IR analysis — one-stop Gemini pipeline that turns a Slack IR export into a comprehensive analysis report in a single command |
| [ir-hub](https://github.com/nlink-jp/ir-hub) | IR lifecycle hub — resident Slack ChatOps bot that opens a channel per case, tracks the response with ACL-gated commands, and ingests messages for postmortems and knowledge reuse (Go) |
| [ir-timeline](https://github.com/nlink-jp/ir-timeline) | IR timeline recorder — single-binary, browser-based tool for tracking IR events with text, images, tags, and time deltas (Go) |
| [ir-tracker](https://github.com/nlink-jp/ir-tracker) | Live IR tracker — continuous ingestion, segmented analysis, and timeline visualization for ongoing incidents via Gemini |
| [mail-triage](https://github.com/nlink-jp/mail-triage) | GCS-based email triage — classifies `.eml`/`.msg` files with Gemini and posts results to Slack; runs as a Cloud Run Job |
| [news-collector](https://github.com/nlink-jp/news-collector) | News collection agent — collects, tags, summarizes, translates, and delivers curated news digests via Gemini + Slack integration |

## Design Philosophy

- **AI-augmented**: Tools use LLMs (Gemini, Claude, OpenAI-compatible endpoints) as the intelligence layer for research and analysis tasks.
- **Structured output**: All tools produce machine-readable JSON alongside human-readable Markdown — suitable for downstream automation.
- **Security-first**: IoC defanging, prompt injection defense, and no-exfiltration-by-default are built-in design constraints.
- **Pipe-friendly**: Tools read from files or stdin and write to files or stdout; composable with `jq` and each other.

## Runtime

Python tools are managed with [uv](https://docs.astral.sh/uv/):

```sh
uv sync && uv run <tool-entrypoint> [args]
```

Go tools build as single binaries:

```sh
make build   # → dist/<tool-name>
```

## Shared Conventions

See [CONVENTIONS.md](https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md) for coding, documentation, and release standards that apply across all tools in this series.
