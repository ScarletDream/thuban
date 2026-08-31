# Thuban

**为长期运行、由 AI 协作维护的项目提供以证据为基础的治理。**

[中文](#中文) · [English](#english)

## 中文

Thuban 帮助编码智能体找到恰当的上下文、尊重文档权威，并把项目改动沉淀成可持续维护的结构，而不是让仓库逐渐堆满交接文档、状态快照和重复指令。

它是一个独立的 [Codex Skill](https://learn.chatgpt.com/docs/build-skills)，不是 OpenAI 产品。

### 名字的由来

[Thuban（天龙座 α 星）](https://dictionary.obspm.fr/terms/thuban/)的传统名称源于阿拉伯语 *ath-thuʿbān*，意为“大蛇”或“巨蛇”。由于地球自转轴的进动，它大约在公元前 2700 年曾非常接近北天极，是古代的北极星。

这个名字也是本项目的设计隐喻：Thuban 不替项目做所有决定，而是为长期协作提供一个稳定的定向基准——让后来进入项目的智能体知道先看哪里、哪些证据代表现实，以及哪些边界不能擅自越过。

### 为什么需要 Thuban

AI 协作项目往往不是突然失败，而是逐渐失控：

- 多份 Markdown 都声称自己代表当前事实；
- 新智能体每次都加载过多上下文，或者读错上下文；
- 实现证据、计划、意图和历史记录混在一起；
- AI 生成的状态文档不断增加；
- 一次清理悄悄改变了权威关系，或者删除了仍有价值的证据；
- 安装更多 Skill 以后，项目又多出一层能力路由问题。

Thuban 把这些视为治理和信息架构问题。它的目标不是总结一切，而是留下一个尽可能小的控制地图，让下一个智能体能在局部做出正确决定。

### 它能做什么

- 为被治理的范围建立一个根 `THUBAN.md`。
- 只有真实的子项目边界确实需要时，才增加局部 `THUBAN.md` 节点。
- 把智能体路由到现有的权威文档，而不是复制内容制造另一份真相。
- 区分已验证的现实、用户意图、执行指令和历史记录。
- 让状态由最小的责任主体持有，而不是创建一份全局交接文档。
- 治理 AI 生成的 Markdown 生命周期：保留、重构、归档、清理或继续调查。
- 对有实质影响的本地治理变更，集中提交一次范围明确的审批包。
- 在发生重要治理写入后，如果环境支持委派，就让一个上下文干净的独立只读智能体执行恢复验收。
- 当项目中的重复证据表明确有必要时，可以维护一份可选的 `THUBAN-SKILLS.md` 能力路由表。

### 它不做什么

- 不会把项目中的每份文档都改写成 Thuban 格式。
- 不会创建通用的 `CURRENT_HANDOFF.md` 或全局 `Next` 队列。
- 不会因为一段文字更新得更晚，就默认它比实现证据更权威。
- 不会擅自整理员工手册、合同、学术记录或其他由人类权威负责的文档。
- 不会在后台持续监控已安装的 Skill 或被治理项目。
- 没有相应授权时，不会执行外部写入或破坏性变更。

### 运行时包

```text
thuban/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── THUBAN-PROTOCOL.md
    └── THUBAN-SKILLS.md
```

被 Thuban 治理的项目只保存该项目自己拥有的治理产物，例如 `THUBAN.md`、可选的 `THUBAN-SKILLS.md`，以及适用 `AGENTS.md` 中的一小段托管引导。项目中不会复制 Skill 运行时文件。

### 安装

可以让 Codex 从本仓库把 Skill 安装到用户级 Skill 目录，也可以手动克隆：

```bash
git clone https://github.com/ScarletDream/thuban.git "$HOME/.agents/skills/thuban"
```

Codex 从 `$HOME/.agents/skills` 读取用户级 Skill，并自动检测 Skill 变更。如果安装或更新后没有出现，重启 Codex。详见 [Codex Skill 官方文档](https://learn.chatgpt.com/docs/build-skills)。

### 使用

在采用或调整项目治理结构时，建议显式调用：

```text
$thuban 以只读方式审计这个仓库。告诉我哪些地方存在权威冲突、
最小而有效的节点结构是什么，以及哪些具体修改需要我审批。
```

其他常用请求：

```text
$thuban 接管这个项目的治理，但不要创建全局交接文件。

$thuban 审计 AI 生成的 Markdown，并提出一个范围明确的生命周期处理方案。

$thuban 检查这个子项目是否需要自己的局部节点。

$thuban 审计项目的 Skill 路由；不要盘点无关的已安装 Skill。
```

当任务符合 Skill 描述时，Thuban 仍可被隐式调用；如果你明确希望采用、重设或迁移某个治理范围，仍建议显式使用 `$thuban`。

Thuban 默认只读分析。凡是涉及治理范围、权威关系、引导指令、节点拓扑、目录结构或破坏性文档处置的变更，都必须先给出准确预览并获得批准。

### 设计原则

1. **先确定归属，再组织信息。** 先判断一项事实由谁负责，再决定放在哪里。
2. **优先路由，不复制真相。** 指向现有责任主体，而不是同步另一份摘要。
3. **状态联邦化。** 局部事实留在局部，只有影响跨越治理边界时才向上汇总。
4. **保守介入。** 责任归属、结构可塑性和出错成本共同决定 Thuban 可以干预多深。
5. **零改动也是有效结果。** 不能用文件是否发生变化来判断治理是否成功。
6. **用恢复能力检验治理。** 一个上下文干净的新智能体，应当无需加载无关分支，就能找到足以支持决策的证据。

### 状态与证据

Thuban 目前处于预发布阶段。在一个独立、非公开的评估工作区中，核心行为已经通过合成样例、真实项目的隔离副本、确定性的结构检查，以及上下文干净的独立审阅者进行测试。这些测试已经发现并修复了权威关系、文档生命周期、标记发现和审阅上下文污染等问题。

本仓库目前只发布运行时包。经过脱敏、可复现的公开评估套件仍在计划中。在它发布之前，请把“适用于所有项目”之类的广泛主张视为尚未证实，并从只读审计开始使用。

### 许可证

[MIT](LICENSE) © 2026 DorimWorks。

---

## English

**Evidence-backed governance for long-lived, AI-assisted projects.**

Thuban helps coding agents recover the right context, respect document authority, and make durable project changes without turning a repository into a pile of handoffs, status snapshots, and duplicated instructions.

It is a standalone [Codex Skill](https://learn.chatgpt.com/docs/build-skills), not an OpenAI product.

### Why the name Thuban?

[Thuban, or Alpha Draconis](https://dictionary.obspm.fr/terms/thuban/), takes its traditional name from the Arabic *ath-thuʿbān*, meaning a large snake or serpent. Because of the precession of Earth's rotational axis, it lay close to the north celestial pole around 2700 BCE and served as an ancient pole star.

The name is also a design metaphor. Thuban does not make every project decision; it provides a stable reference for long-running collaboration, helping the next agent find the right starting point, distinguish evidence from intent or history, and respect boundaries it does not own.

### Why Thuban exists

AI-assisted projects often fail gradually:

- several Markdown files claim to be the current truth;
- every new agent loads too much context or the wrong context;
- implementation evidence, plans, intent, and history are mixed together;
- generated status files keep multiplying;
- a cleanup silently changes authority or deletes useful evidence;
- installing more Skills creates another routing problem instead of solving one.

Thuban treats these as governance and information-architecture problems. Its job is not to summarize everything. Its job is to leave the smallest control map that lets the next agent make the right local decision.

### What it does

- Establishes one root `THUBAN.md` for an adopted scope.
- Adds local `THUBAN.md` nodes only when a real subproject boundary justifies one.
- Routes agents to existing authoritative documents instead of copying them.
- Separates verified reality, user intent, instructions, and history.
- Keeps state federated at the narrowest owner instead of creating one global handoff.
- Governs AI-generated Markdown lifecycle: keep, refactor, archive, clean, or investigate.
- Uses one bounded approval packet for consequential local governance changes.
- Runs independent, read-only, fresh-context recovery acceptance after material governance writes when delegation is available.
- Can maintain an optional `THUBAN-SKILLS.md` capability router when repeated project evidence justifies it.

### What it does not do

- It does not rewrite every project document into a Thuban format.
- It does not create a universal `CURRENT_HANDOFF.md` or global `Next` queue.
- It does not treat newer prose as more authoritative than implementation evidence.
- It does not silently reorganize employee handbooks, contracts, academic records, or other human-authority documents.
- It does not watch installed Skills or governed projects in the background.
- It does not make external writes or destructive changes without the applicable authorization.

### Runtime package

```text
thuban/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── THUBAN-PROTOCOL.md
    └── THUBAN-SKILLS.md
```

Projects governed by Thuban keep only project-owned artifacts such as `THUBAN.md`, an optional `THUBAN-SKILLS.md`, and a small managed bootstrap inside the applicable `AGENTS.md`. They do not receive copies of the Skill runtime.

### Install

Ask Codex to install the Skill from this repository into your user Skill directory, or clone it manually:

```bash
git clone https://github.com/ScarletDream/thuban.git "$HOME/.agents/skills/thuban"
```

Codex reads user Skills from `$HOME/.agents/skills` and detects Skill changes automatically. If an installed update does not appear, restart Codex. See the [official Skill documentation](https://learn.chatgpt.com/docs/build-skills).

### Use

Invoke it explicitly when adopting or changing project governance:

```text
$thuban audit this repository read-only. Tell me where authority conflicts,
what the smallest useful node structure is, and which exact changes would
require my approval.
```

Other useful requests:

```text
$thuban adopt this project without creating a global handoff file.

$thuban audit the AI-generated Markdown and propose one bounded lifecycle packet.

$thuban check whether this subproject needs its own local node.

$thuban audit project Skill routing; do not inventory unrelated installed Skills.
```

Implicit invocation remains enabled when a task matches the Skill description. Explicit `$thuban` invocation is still recommended when you intentionally want to adopt, redesign, or migrate a governance surface.

Thuban defaults to read-only analysis. Changes to scope, authority, bootstrap instructions, topology, directory structure, or destructive document disposition require an exact preview and approval.

### Design principles

1. **Ownership before organization.** Decide who owns a truth before deciding where to place it.
2. **Routes before copies.** Point to an existing owner instead of synchronizing another summary.
3. **Federated state.** Local facts stay local unless their consequences cross a governance boundary.
4. **Conservative action.** Ownership, structure plasticity, and error cost determine how deeply Thuban may intervene.
5. **Zero diff is a valid result.** Governance is not successful merely because files changed.
6. **Recovery is the test.** A fresh agent should reach decision-sufficient evidence without loading unrelated branches.

### Status and evidence

Thuban is pre-release software. In a separate, non-public evaluation workspace, the core behavior has been exercised with synthetic fixtures, isolated copies of real projects, deterministic structure checks, and independent fresh-context reviewers. Those tests have already found and corrected authority, document-lifecycle, marker-discovery, and reviewer-contamination defects.

This repository currently publishes the runtime package only. A sanitized, reproducible public evaluation suite is planned. Until then, treat broad claims about universal project fit as unproven and start with a read-only audit.

### License

[MIT](LICENSE) © 2026 DorimWorks.
