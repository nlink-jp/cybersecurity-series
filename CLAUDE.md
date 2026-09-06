# CLAUDE.md — cybersecurity-series

**Organization rules (mandatory): https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md**

## Non-negotiable rules

- **Tests are mandatory** — write them with the implementation. A feature is not complete without tests.
- **Design for testability** — pure functions, injected dependencies, no untestable globals.
- **Never `go build` directly** — always use `make build` (outputs to `dist/`). `go build` without `-o dist/...` drops the binary in the project root, polluting the working tree.
- **Docs in sync** — update `README.md` and `README.ja.md` in the same commit as behaviour changes.
- **Small, typed commits** — `feat:`, `fix:`, `test:`, `chore:`, `docs:`, `refactor:`, `security:`

## This series

Tools for security investigation, threat intelligence, and incident response — offline-first lookup CLIs + MCP servers alongside AI-assisted analysis tools.

```
cybersecurity-series/
├── abuse-lookup/     github.com/nlink-jp/abuse-lookup     (Go — AbuseIPDB IP reputation CLI + MCP)
├── asn-lookup/       github.com/nlink-jp/asn-lookup       (Go — local IP↔AS lookup CLI + MCP, IPinfo Lite DB)
├── doh-lookup/       github.com/nlink-jp/doh-lookup       (Go — DoH DNS-record lookup CLI + MCP)
├── gti-lookup/       github.com/nlink-jp/gti-lookup       (Go — Google Threat Intelligence context CLI + MCP; Standard tier, commercial licence required)
├── icloud-relay-lookup/ github.com/nlink-jp/icloud-relay-lookup (Go — iCloud Private Relay egress IP lookup CLI + MCP)
├── ir-timeline/      github.com/nlink-jp/ir-timeline      (Go — IR timeline recorder)
├── mac-lookup/       github.com/nlink-jp/mac-lookup       (Go — MAC/BSSID vendor + address-type lookup CLI + MCP)
├── malware-lookup/   github.com/nlink-jp/malware-lookup   (Go — file-hash malware/known-good verdict CLI + MCP)
├── news-collector/   github.com/nlink-jp/news-collector   (Python — news collection + tagging agent)
├── otx-lookup/       github.com/nlink-jp/otx-lookup       (Go — OTX pulse campaign-context lookup + pivot CLI + MCP)
├── rdns-lookup/      github.com/nlink-jp/rdns-lookup      (Go — IP→domains / subdomain / reverse-CNAME lookup CLI + MCP)
├── tor-exit-lookup/  github.com/nlink-jp/tor-exit-lookup  (Go — Tor Exit node lookup CLI + MCP)
└── whois-lookup/     github.com/nlink-jp/whois-lookup     (Go — domain/IP/ASN registration data CLI + MCP)
```

## Release checklist

1. Update `CHANGELOG.md` → commit `chore: release vX.Y.Z` → tag → push
2. `gh release create` (no assets)
3. Build 4 platforms: `linux/amd64`, `linux/arm64`, `darwin/arm64`, `windows/amd64` (darwin is arm64-only)
4. Zip each binary + `README.md` → upload one by one
5. Update umbrella submodule pointer in this repo
6. Update org profile: `nlink-jp/.github/profile/README.md`
