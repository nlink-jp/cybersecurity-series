# CLAUDE.md — cybersecurity-series

**Organization rules (mandatory): https://github.com/nlink-jp/.github/blob/main/CONVENTIONS.md**

## Non-negotiable rules

- **Tests are mandatory** — write them with the implementation. A feature is not complete without tests.
- **Design for testability** — pure functions, injected dependencies, no untestable globals.
- **Docs in sync** — update `README.md` and `README.ja.md` in the same commit as behaviour changes.
- **Small, typed commits** — `feat:`, `fix:`, `test:`, `chore:`, `docs:`, `refactor:`, `security:`

## This series

AI-augmented tools for threat intelligence, product risk assessment, and incident response.

```
cybersecurity-series/
├── ai-ir/            github.com/nlink-jp/ai-ir            (Go — AI incident response analysis)
├── ioc-collector/    github.com/nlink-jp/ioc-collector    (Go — IoC extraction + STIX 2.1)
└── product-research/ github.com/nlink-jp/product-research (Go — product/service risk research)
```

## Release checklist

1. Update `CHANGELOG.md` → commit `chore: release vX.Y.Z` → tag → push
2. `gh release create` (no assets)
3. Build 5 platforms: `linux/amd64`, `linux/arm64`, `darwin/amd64`, `darwin/arm64`, `windows/amd64`
4. Zip each binary + `README.md` → upload one by one
5. Update umbrella submodule pointer in this repo
6. Update org profile: `nlink-jp/.github/profile/README.md`
