# Contributing

There is no product code yet. That makes this the best possible moment to get involved — the decisions being made now are the ones that are expensive to change later.

There are three ways to help, in rough order of how useful they are today.

---

## 1. Nominate a source (Hunter)

The fastest way to make the library deep before launch. Find a component collection out in the wild that is **permissively licensed**, and nominate it.

**Open an issue with the `source-nomination` label.** Include:

- The project name and URL
- A link to the **`LICENSE` file in its repository** (not a marketing page — the actual file)
- Whether it exposes a `shadcn`-compatible registry endpoint, and if so, the exact URL pattern
- Roughly how many components it ships
- Whether there's a paid tier mixed in with the free one

### What we accept

The source code must be under **MIT, Apache-2.0, BSD, ISC, or an equivalent OSI-approved permissive licence**, and that licence must actually permit redistribution of the source with attribution.

### What we turn down

We check every nomination individually, and these get declined regardless of how good the components are:

- **Commons Clause.** "MIT + Commons Clause" is not MIT. Its whole purpose is to prohibit redistributing the software — which is exactly what a registry does. A repository can look MIT-licensed and still carry this, so read the licence file, not the badge.
- **AGPL-3.0.** Its copyleft propagates to the combined work, which would pull an entire permissive registry under AGPL obligations.
- **Bespoke licences that prohibit redistributing source.** Some of the most visually striking collections are licensed this way. They are off the table.
- **"Free for personal use", or anything requiring a commercial licence we don't have.**
- **Content scraped from another component marketplace.** A component's own licence does not override the platform terms under which it was published.

If a nomination is declined, it gets recorded with the reason and the quoted licence text, so nobody has to re-litigate it later. That record is not a judgement about the project — several of these are excellent, and we'd happily link to them.

### What happens next

Accepted nominations get imported with a pinned upstream commit SHA, a snapshot of the licence text as it read on the day of import, and full attribution to the original author. If you're the original author, you can claim the listing and it becomes yours.

---

## 2. Publish a component (Creator)

We are especially interested in **Vue 3 and Nuxt** components, because that is the gap this project exists to close. If you have components you'd like to publish at launch, open an issue with the `creator-interest` label, or reach out directly.

Authorship is yours. You keep the credit, the profile and the install count.

---

## 3. Code

Stack, for when the repository has code in it:

- **Monorepo** — Turborepo + pnpm
- **Web** — Next.js 15 (App Router), TypeScript, Tailwind, Supabase (Postgres + RLS)
- **Sandbox** — separate origin, browser-side `esbuild-wasm` runtime
- **Media worker** — Node + Playwright for automated previews
- **CLI / MCP** — TypeScript, published to npm

Contributing guidelines for code will land with Phase 1. If you want to help build it, open an issue with the `code-interest` label and say what you'd like to work on.

---

## Ground rules

- **Licence accuracy beats speed.** An import without verified provenance is a liability, not a component.
- **Attribution is not optional.** If you cannot name the original author, the import does not ship.
- **Say what you don't know.** "Unverified" is a useful answer. A confident guess that turns out to be wrong costs more than the time it saved.
- Be decent to each other. This is a community project about other people's work.

---

## 中文速览

目前还没有产品代码，所以现在正是参与的最好时机。

**三种参与方式：**

1. **提名素材源（猎人）**：用 `source-nomination` 标签开 issue，附上项目地址、仓库里**真实的 LICENSE 文件链接**（不是宣传页）、是否提供 shadcn 兼容的注册表端点、大致组件数量、是否混有付费层。
2. **投稿组件（创作者）**：我们尤其需要 **Vue 3 / Nuxt** 组件，因为这正是本项目的立项理由。作者身份归你，荣誉归你。
3. **参与开发（代码）**：技术栈为 Turborepo + pnpm / Next.js 15 / 独立域名沙盒 / Playwright / TypeScript。用 `code-interest` 标签开 issue 说明你想做什么。

**我们不接受的内容（逐条核实，无论组件多好看）：**

- **Commons Clause** —— "MIT + Commons Clause" 不是 MIT，它的目的就是禁止再分发软件，而注册表做的恰恰就是这个。仓库看起来是 MIT 也可能暗藏此条款，所以要读许可证文件而不是看徽章。
- **AGPL-3.0** —— 传染性会把整个宽松许可的注册表拖入 AGPL 义务。
- **禁止再分发源文件的自定义许可** —— 一些视觉效果最惊艳的组件库正是此类。
- **"仅限个人使用"**，或需要我们没有的商业授权。
- **从其他组件市场抓取的内容** —— 组件自身的许可不能覆盖其发布时所受的平台条款。

被拒绝的提名会连同理由和许可证原文一并记录，避免以后反复争论。这份记录不构成对项目本身的评价——其中有好几个非常优秀，我们很乐意链接它们。

**底线：** 许可准确性优先于速度；署名不可省略——叫不出原作者就别发布；不知道就说不知道，"未核实"是有价值的答案。
