# NPXUI

**The open-source UI registry you can `npx` into any project — React and Vue.**

```bash
npx npxui add @alice/glow-button
npx npxui add @alice/glow-button --vue
```

`npxui` writes a component's **source code** into your project. No black-box dependency, no version lock-in, no wrapper you have to fight. You get the code, you own the code, and you can walk away from the registry the moment you're done with it.

> **Status: pre-launch.** This repository is the project home. Nothing is published to npm yet, and the roadmap below is a plan — not a description of what exists today. Star / Watch to follow along.

---

## Why

Component libraries have traditionally been one of two things: a package you import, which locks you to its API forever; or a website you copy from, with no way to ever receive an update. shadcn/ui proved there is a third way — **the registry**: a machine-readable index of source code that a CLI injects directly into your project.

That ecosystem is healthy and growing fast. But it has two obvious gaps.

**It is almost entirely React.** If you write Vue 3 or Nuxt, the best new components simply aren't available to you. You port them by hand, or you do without.

**Its AI-facing layer is becoming paywalled.** The newest way to build UI is to ask your editor for it. When that layer is a metered subscription that resets monthly, it stops being infrastructure.

NPXUI is built on the registry model, and takes a position on both.

---

## What we're building

| | |
| :--- | :--- |
| **One registry, two ecosystems** | React and Vue 3 / Nuxt as first-class citizens — not a port, not an afterthought. `--vue` on every install. |
| **Free MCP, permanently** | `@npxui/mcp` for Cursor / Windsurf / Claude Code. Search and pull source: free, open, no call quota, no monthly reset. Bring your own key if you want AI rewriting. |
| **Bundle size on the card** | Every component shows its measured Gzipped size and flags heavy dependencies. Anything pulling in Three.js or Spline gets a warning *before* it lands in your bundle, not after. |
| **Live props controls** | Your TypeScript `interface Props` is parsed into a real control panel on the detail page. Tweak the props, see the result, copy the parameterised JSX. |
| **An install path that can't break** | The base registry is mirrored, so an install never depends on a third-party CDN being reachable from where you are. |
| **React → Vue transpilation** | For components that only exist in React, an AST + LLM pipeline generates and validates a Vue 3 equivalent. |

## What we won't do

This part matters more than the feature list, which is why it's up here instead of buried at the bottom.

- **We don't scrape competing registries.** A number of popular component collections are licensed in ways that forbid re-hosting their source — Commons Clause, AGPL, and bespoke licences that explicitly prohibit redistributing source files. We check every source individually and we leave those alone, no matter how popular they are.
- **We don't re-host anyone's work without provenance.** Every imported component pins an upstream commit SHA and carries a snapshot of the licence text *as it read at import time*. Licences change. A pinned commit plus a snapshot is the only thing that makes an import defensible years later.
- **We don't strip attribution.** Copyright notices travel with the source into your project — the CLI writes an `NPXUI_ATTRIBUTION.md` next to the files it installs.
- **We don't meter the community registry.** No subscription to search, no quota to install, and no Pro tier gating access to what the community contributed.

## The two roles

Borrowed from how the best of these communities bootstrapped, and it's how you can help before a single line of product code exists.

**Creators** publish original components. You keep authorship, you get the profile, the install count and the credit. The `/publish` workbench — Monaco editor with live AST validation on the left, live sandbox preview on the right — is on the roadmap.

**Hunters** find a great permissively-licensed component out in the wild, package it into registry format, and credit the original author. When that author shows up, they can claim the listing and it becomes theirs. This is how the early library gets deep before the creators arrive.

If you have components of your own — **especially Vue** — we would like to talk to you before launch. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Roadmap

Full detail in [ROADMAP.md](ROADMAP.md).

- [ ] **Phase 1** — Registry API, component detail pages, `npxui` CLI, AI IDE prompt export
- [ ] **Phase 2** — `/publish` workbench, isolated sandbox origin, AST safety checks
- [ ] **Phase 3** — Automated preview / screencast pipeline, Vue 3 transpilation
- [ ] **Phase 4** — `@npxui/mcp`, creator incentives, template marketplace

---

## 中文说明

**NPXUI（新派 UI）—— 一行 `npx` 命令，把社区共创的高颜值 UI 源码直接注入你的项目。**

```bash
npx npxui add @alice/glow-button          # React
npx npxui add @alice/glow-button --vue    # Vue 3
```

`npxui` 做的是把组件的**源码**写进你的项目，而不是让你装一个黑盒依赖。代码到手就是你的，随时可改，用完可以彻底脱离注册表。

**当前状态：尚在启动前。** 本仓库是项目主页，npm 上还没有发布任何东西，下面的路线图是计划而非现状。

**我们要解决的两个问题。** 一是这个生态几乎全是 React，写 Vue 3 / Nuxt 的人拿不到最好的新组件；二是面向 AI 的那一层正在变成按次计费的订阅，一旦月底清零，就不再算基础设施。

**我们的承诺。** MCP 检索与拉取源码永久免费；卡片上直接标注实测 Gzip 体积与重依赖预警；TypeScript 接口自动生成实时 Props 调节面板；基础注册表本地镜像，安装链路不依赖第三方 CDN 是否可达。

**我们不做的事。** 不抓取竞争注册表——部分流行组件库的许可明确禁止再分发其源码（Commons Clause、AGPL，以及禁止再分发源文件的自定义许可），我们逐源核实，无论多流行都不收；不在没有溯源的情况下搬运——每个导入组件锁定上游 commit SHA，并留存导入当时的许可证全文快照；不抹除署名——版权声明随源码一同写入你的项目；不把社区注册表做成收费墙。

**两种参与角色。** **创作者**发布原创组件，保留作者身份与全部荣誉；**猎人**把散落在各处的宽松许可好组件标准化打包并标注原作者，原作者入驻后可一键认领。如果你手上有组件——**尤其是 Vue 的**——我们希望在发布之前就联系你。

---

## Licence

MIT — see [LICENSE](LICENSE).

Imported third-party components retain their own licences and attribution. Nothing in this repository's licence applies to them.
