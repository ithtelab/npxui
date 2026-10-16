# Roadmap

This is a plan, not a changelog. Nothing here is built yet. Timelines are deliberately absent — scope is honest, dates would not be.

Legend: `[ ]` planned · `[~]` in progress · `[x]` done

---

## Phase 1 — The loop closes

The smallest thing that is actually useful: find a component, install it, get working source.

- [ ] Registry JSON API — `shadcn`-compatible `registry-item.json` served per component, with a `?framework=react|vue` switch
- [ ] Component detail page — live preview, light/dark toggle, source file tree, install command copy
- [ ] `npxui` CLI — `npx npxui add @user/component`, package-manager detection, conflict prompts
- [ ] AI IDE prompt export — one-click structured prompt (source + dependencies + usage) for Cursor / Windsurf / Trae / v0 / Bolt, in both English and Chinese
- [ ] Base registry mirror — `shadcn/ui` and `shadcn-vue` served locally so `registryDependencies` resolve without leaving the registry
- [ ] Vetted initial library — permissively-licensed sources imported with pinned commit SHA + licence snapshot + attribution, each individually verified

**Exit criteria:** a developer in any network can run one command and get working, attributed source code.

## Phase 2 — Creators arrive

- [ ] `/publish` workbench — Monaco editor with live AST validation, live sandbox preview beside it
- [ ] Isolated sandbox origin — separate domain, so rendering untrusted submitted code can never reach main-site credentials
- [ ] AST safety gate — dependency extraction, forbidden-API interception, and a clear statement of what static analysis *cannot* catch
- [ ] Review state machine — `on_review` → `posted` → `featured`
- [ ] Attribution propagation — installed files carry a copyright header, project root gets an idempotent `NPXUI_ATTRIBUTION.md`

**Exit criteria:** a stranger can publish a component and have it reviewed without a maintainer touching the repository.

## Phase 3 — It runs itself

- [ ] Automated preview pipeline — headless browser captures light/dark covers plus a short hover screencast for every component, uploaded to object storage
- [ ] Bundle size measurement — Gzipped size and heavy-dependency flags computed at publish time
- [ ] Props schema extraction — TypeScript interfaces parsed into a live control panel
- [ ] Vue 3 transpilation — AST + LLM pipeline that generates and validates a Vue equivalent for React-only components
- [ ] Licence drift monitoring — weekly re-check of every upstream licence; a changed hash or a repository redirect quarantines the affected imports automatically

**Exit criteria:** publishing a component produces correct previews, correct size numbers and a working Vue version with no human in the loop.

## Phase 4 — Ecosystem

- [ ] `@npxui/mcp` — natural-language component search and install from inside Cursor / Windsurf / Claude Code
- [ ] Creator incentives — featured rotation, install leaderboards, revenue share for template collections
- [ ] Community hunting — the ingestion tooling opened up so anyone can package and nominate a source
- [ ] Curated verticals — Chinese typography, AI chat workflows, data dashboards

---

## Explicitly out of scope

These get asked for often enough that it's worth saying no in advance.

- **A paid tier on the community registry.** Access to what the community contributed is not a product to sell. Pro features, if they exist, will be things like hosted private registries.
- **Importing from sources whose licences forbid it.** See the note in the [README](README.md#what-we-wont-do). A deep library is worthless if it can't be defended.
- **A proprietary component format.** The registry speaks the `shadcn` protocol. If we disappeared tomorrow, everything you installed should still work.

---

## 中文速览

- **阶段一 · 闭环跑通**：注册表 JSON 接口、组件详情页、`npxui` CLI、AI IDE 提示词导出、基础注册表本地镜像、首批经逐源核实的许可干净组件。
- **阶段二 · 创作者进场**：`/publish` 在线工作台、独立域名沙盒、AST 安全闸门、三级审核状态机、署名随源码注入。
- **阶段三 · 自动运转**：自动截图与录屏、包体积测算、Props 自动解析为调节面板、React→Vue 转译、许可证漂移监控。
- **阶段四 · 生态**：`@npxui/mcp`、创作者激励、开放社区狩猎、垂直专区。

**明确不做**：社区注册表上的付费墙；导入许可禁止再分发的内容；私有组件格式。
