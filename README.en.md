<div align="center">

# NPXUI

**The open-source UI registry · React and Vue 3**

A component registry for React and Vue 3 / Nuxt: one command writes a component's **source code** into your project instead of installing a black-box dependency. MCP search and source retrieval for AI editors are free forever. The base registry is mirrored, so an install never depends on a third-party CDN being reachable.

![Next.js](https://img.shields.io/badge/Next.js-15-000000?logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white)
![Vue 3](https://img.shields.io/badge/Vue_3-supported-4FC08D?logo=vuedotjs&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?logo=tailwindcss&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-22c55e)

![Status](https://img.shields.io/badge/status-pre--launch-f59e0b)
[![Roadmap](https://img.shields.io/badge/roadmap-ROADMAP-blue)](ROADMAP.md)
[![Contributing](https://img.shields.io/badge/contributing-CONTRIBUTING-5319e7)](CONTRIBUTING.md)
[![Issues](https://img.shields.io/github/issues/ithtelab/npxui?color=f59e0b&label=issues)](https://github.com/ithtelab/npxui/issues)

**English** · [简体中文](README.md) ｜ Published and discussed in the [LINUX DO](https://linux.do) community

<a href="https://github.com/ithtelab/npxui"><img src="docs/images/hero.svg" alt="NPXUI" width="100%" /></a>

</div>

---

## What this is

When you want to add a good-looking component to a project, the choices today are: install a package and live inside its API forever, or copy source off a component site and then patch the dependencies, the config and the import paths yourself — with no way to hear about it when the original is updated.

shadcn/ui proved there's a third option: **the registry**. A machine-readable index of source code that a CLI injects straight into your project. The code lands in your repo, it's yours, you can change it, and you can walk away from the registry the moment you're done.

That ecosystem is healthy, but it has two obvious gaps, and this project exists because of them:

| The gap | What NPXUI does |
|---|---|
| **It's almost entirely React.** If you write Vue 3 or Nuxt, the best new components simply aren't available to you — you port them by hand, or you do without. | One registry, two ecosystems. Pass `--vue` and get the Vue 3 build. Native Vue implementations get imported first; transpilation is a fallback, not the plan. |
| **The AI-facing layer is going paid.** When it's metered per call and resets monthly, it stops being infrastructure. | `@npxui/mcp` search and source retrieval are free forever — no quota, no monthly reset. |

In one line: **the registry speaks the shadcn protocol, Vue 3 is a first-class citizen, and the AI interface has no paywall.**

---

## Relationship to the shadcn ecosystem

This project follows the shadcn registry protocol and **does not invent a format**:

- **Wire-compatible** — every component is served as a standard `registry-item.json`, so `npx shadcn@latest add <URL>` installs our components too
- **Base components mirrored locally** — every `registryDependencies` entry (`button`, `card`, `dialog`, …) resolves to a local mirror, so nothing depends on `ui.shadcn.com` or any third-party asset host being reachable
- **Non-invasive** — we don't ask shadcn to change a line of code, and we don't fork its base components
- **You can leave** — what lands in your project is plain source. Nothing at runtime goes through this platform. If NPXUI shut down tomorrow, everything you installed still works

---

## Features

### Discovery and preview

- **Natural-language search** — `Cmd+K` and type the situation, not a keyword. Vector search blended with keyword matching, weighted by install count
- **Zero-jank hover motion** — the list shows a static cover and plays a 60fps motion clip on hover. Covers and clips are pre-recorded by a headless browser, rather than mounting a live `iframe` per card
- **Dual themes and responsive** — toggle light / dark on the detail page, drag the viewport to test breakpoints
- **Live props controls** — TypeScript interfaces are parsed into real controls; copy the parameterised call when you're happy with it
- **Size transparency** — measured Gzipped size on every card and detail page, with a warning on anything dragging in something like Three.js

### Install and injection

- **One command** — `npx npxui add @user/comp`, and `shadcn add <URL>` works too
- **Dependencies handled** — an AST pass extracts npm and base-component dependencies, and detects whether you're on npm / pnpm / yarn / bun
- **Config merged, not described** — Tailwind extensions and light/dark CSS variables are written into the right files instead of handed to you as instructions
- **Attribution travels with the code** — copyright headers are written into the installed files, and an `NPXUI_ATTRIBUTION.md` appears at your project root

### Cross-framework

- **Vue 3 / Nuxt as a first-class citizen** — the `--vue` flag, with native `shadcn-vue` protocol support
- **Native Vue sources first** — where a native Vue implementation already exists, we import that rather than make you wait on transpilation
- **React → Vue transpilation as a fallback** — only for components that are React-only, and only published after the AST + LLM output passes validation

### AI interface

- **MCP, free forever** — `@npxui/mcp` for Cursor / Windsurf / Claude Code. Search and source retrieval with no quota and no monthly reset
- **Bring your own key** — if you want AI rewriting, use your own API key. We don't resell models
- **Prompt export** — bilingual, tuned for Cursor / Windsurf / Trae / v0 / Bolt

---

## Status

**This project is pre-launch: nothing is published to npm and there is no installable version.** This repository is the project home — what's public here is the design, the roadmap, and the rules for contributing.

The **intended** interaction for the commands above looks roughly like this (not yet implemented — it's written out so the design can be argued with):

```bash
$ npx npxui add @alice/glow-button
✔ Detected pnpm-lock.yaml, using pnpm
✔ Wrote src/components/ui/glow-button.tsx
✔ Wrote src/components/ui/glow-button.helpers.ts
✔ Merged keyframes and animation into tailwind.config.ts
✔ Installed framer-motion@^11
✔ Generated NPXUI_ATTRIBUTION.md (original author + full licence text)
✨ Done. The source is in your project — change it however you like.
```

---

## Roadmap

| Phase | Contents | Status |
|---|---|---|
| **1 · The loop closes** | Registry JSON API, component detail pages, `npxui` CLI, AI prompt export, mirrored base registry, a first batch of per-source licence-verified components | Planned |
| **2 · Creators arrive** | `/publish` workbench (Monaco + live AST validation + live preview), isolated sandbox origin, three-stage review | Planned |
| **3 · It runs itself** | Automated screenshot and screencast pipeline, bundle-size measurement, props schema extraction, React → Vue transpilation, licence drift monitoring | Planned |
| **4 · Ecosystem** | `@npxui/mcp`, creator incentives, community source hunting, curated verticals | Planned |

Details, exit criteria and the explicit out-of-scope list are in [ROADMAP.md](ROADMAP.md).

---

## What we won't do

This part matters more than the feature list, which is why it's up here instead of buried at the bottom:

- **We don't scrape competing registries.** A number of popular component collections are licensed in ways that forbid re-hosting their source — Commons Clause, AGPL-3.0, and bespoke licences that prohibit redistributing source files. We check every source individually and leave those alone, no matter how popular they are
- **We don't re-host anyone's work without provenance.** Every imported component pins an upstream commit SHA and carries a snapshot of the licence text as it read at import time. Licences change; a repository URL on its own isn't enough
- **We don't strip attribution.** Copyright notices travel with the source into your project
- **We don't meter the community registry.** No quota on search or install, and no Pro tier that gates access to what the community contributed
- **We don't lock you into a private format.** The wire format is the shadcn protocol, what you install is plain source, and it keeps working if we disappear

---

## Contributing

Three ways in, ordered by what's most needed right now:

**1. Nominate a source (Hunter)** — find a permissively-licensed component collection and nominate it. Include a link to the **actual `LICENSE` file in its repository** (not a marketing page) and whether it exposes a shadcn-compatible registry endpoint. The bar and the rejection criteria are in [CONTRIBUTING.md](CONTRIBUTING.md).

**2. Publish a component (Creator)** — we especially want **Vue 3 / Nuxt** components, because that's the gap this project exists to close. Authorship, profile and install counts are yours.

**3. Write code** — stack: Turborepo + pnpm · Next.js 15 App Router · isolated sandbox origin (`esbuild-wasm`) · Playwright media pipeline · Supabase Postgres with RLS. Open an issue with the `code-interest` label and say what you'd like to work on.

---

## Documentation

- [ROADMAP.md](ROADMAP.md) — four phases, exit criteria, and the explicit out-of-scope list
- [CONTRIBUTING.md](CONTRIBUTING.md) — nomination and submission process, licence bar and rejection criteria
- [LICENSE](LICENSE) — MIT

---

## Credits

- [**shadcn/ui**](https://github.com/shadcn-ui/ui) (MIT) — the de facto registry protocol; our public interface follows it exactly
- [**shadcn-vue**](https://github.com/unovue/shadcn-vue) (MIT) — the protocol implementation on the Vue side
- [**LINUX DO**](https://linux.do) — the community where this project is published and discussed

> Third-party components imported in future keep their own licences and attribution; this repository's licence does not apply to them.

---

## Licence

[MIT](LICENSE)
