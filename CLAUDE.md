# CLAUDE.md — cybersecurity-series

**Organization rules (mandatory): https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md**

## Non-negotiable rules

- **Tests are mandatory** — write them with the implementation. A feature is not complete without tests.
- **Design for testability** — pure functions, injected dependencies, no untestable globals.
- **Never `go build` directly** — always use `make build` (outputs to `dist/`). `go build` without `-o dist/...` drops the binary in the project root, polluting the working tree.
- **Docs in sync** — update `README.md` and `README.ja.md` in the same commit as behaviour changes.
- **Small, typed commits** — `feat:`, `fix:`, `test:`, `chore:`, `docs:`, `refactor:`, `security:`

## This series

AI-augmented tools for threat intelligence, product risk assessment, and incident response.

```
cybersecurity-series/
├── abuse-lookup/     github.com/nlink-jp/abuse-lookup     (Go — AbuseIPDB IP reputation CLI + MCP)
├── ai-ir/            github.com/nlink-jp/ai-ir            (Go — AI incident response analysis)
├── ai-ir2/           github.com/nlink-jp/ai-ir2           (Python — next-gen one-stop IR analysis)
├── cti-graph/        github.com/nlink-jp/cti-graph        (Python — local attack graph analysis; archived)
├── cti-primer/       github.com/nlink-jp/cti-primer       (Python — local-first PIR generation; archived)
├── doh-lookup/       github.com/nlink-jp/doh-lookup       (Go — DoH DNS-record lookup CLI + MCP)
├── icloud-relay-lookup/ github.com/nlink-jp/icloud-relay-lookup (Go — iCloud Private Relay egress IP lookup CLI + MCP)
├── ioc-collector/    github.com/nlink-jp/ioc-collector    (Go — IoC extraction + STIX 2.1)
├── ir-hub/           github.com/nlink-jp/ir-hub           (Go — IR lifecycle hub Slack bot)
├── ir-timeline/      github.com/nlink-jp/ir-timeline      (Go — IR timeline recorder)
├── ir-tracker/       github.com/nlink-jp/ir-tracker       (Python — live IR tracker + timeline)
├── mac-lookup/       github.com/nlink-jp/mac-lookup       (Go — MAC/BSSID vendor + address-type lookup CLI + MCP)
├── mail-triage/      github.com/nlink-jp/mail-triage      (Python — GCS email triage via Gemini; archived)
├── malware-lookup/   github.com/nlink-jp/malware-lookup   (Go — file-hash malware/known-good verdict CLI + MCP)
├── news-collector/   github.com/nlink-jp/news-collector   (Python — news collection + tagging agent)
├── product-research/ github.com/nlink-jp/product-research (Python — product/service risk research)
├── rdns-lookup/      github.com/nlink-jp/rdns-lookup      (Go — IP→domains / subdomain / reverse-CNAME lookup CLI + MCP)
├── tor-exit-lookup/  github.com/nlink-jp/tor-exit-lookup  (Go — Tor Exit node lookup CLI + MCP)
└── whois-lookup/     github.com/nlink-jp/whois-lookup     (Go — domain/IP/ASN registration data CLI + MCP)
```

## Release checklist

1. Update `CHANGELOG.md` → commit `chore: release vX.Y.Z` → tag → push
2. `gh release create` (no assets)
3. Build 5 platforms: `linux/amd64`, `linux/arm64`, `darwin/amd64`, `darwin/arm64`, `windows/amd64`
4. Zip each binary + `README.md` → upload one by one
5. Update umbrella submodule pointer in this repo
6. Update org profile: `nlink-jp/.github/profile/README.md`
