# Thuban

**Evidence-backed governance for long-lived, AI-assisted projects.**

Thuban helps coding agents recover the right context, respect document authority, and make durable project changes without turning a repository into a pile of handoffs, status snapshots, and duplicated instructions.

It is a standalone [Codex Skill](https://learn.chatgpt.com/docs/build-skills), not an OpenAI product.

## Why Thuban exists

AI-assisted projects often fail gradually:

- several Markdown files claim to be the current truth;
- every new agent loads too much context or the wrong context;
- implementation evidence, plans, intent, and history are mixed together;
- generated status files keep multiplying;
- a cleanup silently changes authority or deletes useful evidence;
- installing more Skills creates another routing problem instead of solving one.

Thuban treats these as governance and information-architecture problems. Its job is not to summarize everything. Its job is to leave the smallest control map that lets the next agent make the right local decision.

## What it does

- Establishes one root `THUBAN.md` for an adopted scope.
- Adds local `THUBAN.md` nodes only when a real subproject boundary justifies one.
- Routes agents to existing authoritative documents instead of copying them.
- Separates verified reality, user intent, instructions, and history.
- Keeps state federated at the narrowest owner instead of creating one global handoff.
- Governs AI-generated Markdown lifecycle: keep, refactor, archive, clean, or investigate.
- Uses one bounded approval packet for consequential local governance changes.
- Runs independent, read-only, fresh-context recovery acceptance after material governance writes when delegation is available.
- Can maintain an optional `THUBAN-SKILLS.md` capability router when repeated project evidence justifies it.

## What it does not do

- It does not rewrite every project document into a Thuban format.
- It does not create a universal `CURRENT_HANDOFF.md` or global `Next` queue.
- It does not treat newer prose as more authoritative than implementation evidence.
- It does not silently reorganize employee handbooks, contracts, academic records, or other human-authority documents.
- It does not watch installed Skills or governed projects in the background.
- It does not make external writes or destructive changes without the applicable authorization.

## Runtime package

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

## Install

Ask Codex to install the Skill from this repository into your user Skill directory, or clone it manually:

```bash
git clone https://github.com/ScarletDream/thuban.git "$HOME/.agents/skills/thuban"
```

Codex reads user Skills from `$HOME/.agents/skills` and detects Skill changes automatically. If an installed update does not appear, restart Codex. See the [official Skill documentation](https://learn.chatgpt.com/docs/build-skills).

## Use

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

## Design principles

1. **Ownership before organization.** Decide who owns a truth before deciding where to place it.
2. **Routes before copies.** Point to an existing owner instead of synchronizing another summary.
3. **Federated state.** Local facts stay local unless their consequences cross a governance boundary.
4. **Conservative action.** Ownership, structure plasticity, and error cost determine how deeply Thuban may intervene.
5. **Zero diff is a valid result.** Governance is not successful merely because files changed.
6. **Recovery is the test.** A fresh agent should reach decision-sufficient evidence without loading unrelated branches.

## Status and evidence

Thuban is pre-release software. In a separate, non-public evaluation workspace, the core behavior has been exercised with synthetic fixtures, isolated copies of real projects, deterministic structure checks, and independent fresh-context reviewers. Those tests have already found and corrected authority, document-lifecycle, marker-discovery, and reviewer-contamination defects.

This repository currently publishes the runtime package only. A sanitized, reproducible public evaluation suite is planned. Until then, treat broad claims about universal project fit as unproven and start with a read-only audit.

## License

[MIT](LICENSE) © 2026 DorimWorks.
