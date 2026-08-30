<!-- THUBAN:PROTOCOL v1 -->

# Thuban node protocol

Load this reference only when adopting, changing, or auditing Thuban's project-owned governance surface.

## Identity

| Role | File | Required marker |
|---|---|---|
| Root or local node | `THUBAN.md` | `<!-- THUBAN:NODE v1 -->` |
| Optional Skill router | `THUBAN-SKILLS.md` | `<!-- THUBAN:SKILLS v1 -->` |
| `AGENTS.md` bootstrap block | applicable existing or approved new minimal `AGENTS.md` | `<!-- THUBAN:BOOTSTRAP v1 -->` … `<!-- /THUBAN:BOOTSTRAP -->` |

The marker requirement applies only to Thuban-owned project documents and its managed bootstrap block. Registered project documents retain their names and contents.

## Topology

- Every adopted scope has one root node at that scope's root. This is not a one-node-per-project limit: justified local scopes may each contain their own `THUBAN.md`.
- Each local node has one parent node. This forms the governance ownership tree.
- The direct parent must route to every local child under an observable read condition. A child's `Parent` backlink does not make it reachable from root.
- Routes may point across branches when a task genuinely needs another scope. Keep this read graph sparse.
- A directory being important is not enough to justify a node. Add one only when it owns distinct decisions, authority, local state, or a recurring route set whose saved decision cost exceeds maintenance cost.
- Never write nodes inside external hosts, dependencies, vendor trees, generated outputs, caches, or unowned areas. Register the boundary in the nearest owned node.

## Node contract

Use the project's language. Omit empty optional sections.

```markdown
<!-- THUBAN:NODE v1 -->

# Thuban — <scope>

## Scope
- Owns: <exact boundary>
- Excludes: <only confusing adjacent areas>
- Parent: <node path, omitted at root>

## Contract
- <non-obvious invariant, authority assignment, or decision boundary>

## State
- <verified local fact, blocker, or next transition with evidence when useful>

## Routes
| Read when | Path | Truth owned / contribution |
|---|---|---|
| <observable condition> | `<exact path>` | <subject> · <reality / intent / instruction / history / reference / child node> |
```

`Scope` is required. `Contract`, `State`, and `Routes` exist only when they change a future decision.

### Contract

Record only information whose omission would predictably cause a wrong action: preserved constraints, subject-specific truth authority, ownership boundaries, approval gates, or counterintuitive invariants. A source of truth may be one artifact or an explicit evidence set such as implementation plus contract tests.

### State

State is federated. A local node owns facts and explicitly chosen next transitions local to its scope. The root records only consequences that cross scopes or change the project-level decision. Do not duplicate local state at the root, and do not require every node to have state.

Record natural verification dates only for facts that become unsafe when time-sensitive, such as deployments or external-provider capabilities. Do not date every entry.

### Routes and document registry

A route answers three questions: when should this be read, where is it, and which subject/truth does it own or contribute? Use cells such as `cross-post title preference · intent`, `deployed API behavior · reality`, or `web scope · child node`. Register important existing Markdown here rather than copying or renaming it. A document may own intent while code and tests own current reality; record both instead of forcing a false winner.

Route the nearest authoritative gateway, not leaves it can discover. Several routes into one area signal compression or a justified child. Routine manifests and task-local artifacts need no root route unless they carry a non-obvious cross-scope decision.

A route target is one concrete file or child node, not a directory pattern. Represent one gateway once and combine its related read conditions in that row. When an existing index or lifecycle document selects the relevant Idea, post, or research artifact, route that gateway instead of adding a generic area route.

When the correct gateway is large, keep the route target as the concrete file and name a stable heading or search term in the read condition or truth contribution. Read that section first and expand only when the decision requires it. Do not create another index solely to compensate for one long file unless repeated recovery cost proves a durable gateway is needed.

Scope search commands to the routed files and owned paths needed for the decision. A broad recursive search is a fallback after routed evidence is insufficient; it must exclude external, generated, vendored, private, and unrelated instruction or Skill areas unless the task concerns them.

`AGENTS.md` is already the effective instruction surface and bootstrap. Preserve its retained authority in `Contract`; do not route back to it from `THUBAN.md`.

Use routes for child nodes and cross-scope dependencies. During one task, read a target at most once, follow a cross-route only when the current decision requires it, and stop when evidence is decision-sufficient; do not recursively traverse links.

## Durable document restraint

Before creating a durable project Markdown, first locate the existing owner for that subject. Create a new document only when the agent can name its distinct subject owner, recurring reader or trigger, lifecycle, and what it replaces or why no owner fits. State this briefly in a consequential proposal or completion report; do not add ceremonial metadata to every document.

Keep transient reasoning, scratch research, and conversation notes outside the durable project surface or in an ignored task-temporary area. Remove only temporary artifacts created by the current task. Do not create a default handoff, memory, latest-status, dated summary, or audit ledger merely to record activity.

Authorship is not a disposition rule. An agent-written acceptance record may be durable evidence, while a human-written current-status note may be stale. Decide from subject ownership, truth role, recurring consumers, evidence value, lifecycle, and recovery cost.

Documents whose authority derives from people or an organization rather than project mechanics—such as employee handbooks, HR or legal policy, contracts, signed records, academic deliverables, or personal archives—are protected. Audit them read-only by default; do not rewrite, rename, reorganize, or archive them to remove drift or improve style. A current request that explicitly includes editing such a document is sufficient authority for that ordinary edit; require another preview only when governance, structure, authority, or destructive disposition also changes.

### Write-side document lifecycle

When the task includes consolidating, archiving, or cleaning project documents:

1. Inventory the exact candidates and all known consumers, links, startup instructions, generated copies, and omitted or external areas. A complete search inside a partial fixture is not evidence about consumers that the fixture excludes.
2. Assign each durable subject an existing owner and truth role. Route verified reality to its evidence owner, intent to its approved plan or specification, and useful past claims to an existing history owner. Do not promote an unverified summary into reality merely while merging it.
3. Extract only unique, still-useful content. Remove duplicate live claims instead of synchronizing another summary. Preserve a historical file only when its provenance or traceability has a real recurring consumer; Git history alone is often the cheaper recovery path.
4. Present one exact packet for structural or destructive work: edits, moves or removals, consumer updates, authority effects, recovery path, and explicit exclusions. An explicitly requested in-place content edit needs no extra confirmation unless it also changes governance, structure, authority, or destructive disposition.
5. Apply the approved packet as one bounded change. Do not leave redirect stubs unless a verified live consumer cannot be updated atomically.
6. Validate that all known consumers resolve, every active subject has one clear owner, current-looking names and headings no longer expose historical claims as live truth, protected documents are unchanged, recovery works, and the actual write set matches the packet. If evidence becomes incomplete, stop at refactor or archive; do not escalate to clean.

## Narrow runtime maintenance

The root node contains this compact rule, adapted only for path names:

```markdown
## Maintenance

After authorized work, Codex may sync only facts the task directly verified, plus a mechanically moved route path when no `THUBAN.md` moved and its meaning is unchanged. Status evidence does not authorize adding, removing, or changing priority, queue membership, or `Next`; those require the user or an approved plan. Any node-bearing move or change to Scope, Contract, authority, route meaning, topology, Skill routing, or bootstrap requires `$thuban` and an exact preview.
```

Local nodes inherit this rule; do not duplicate it.

## `AGENTS.md` bootstrap

`AGENTS.md` is a persistent instruction surface, not a Thuban node. First inspect its ownership, precedence, effective instruction chain, and existing content. Present the exact managed block and placement before editing it.

If no applicable project-owned `AGENTS.md` exists, active adoption may propose one minimal file containing the managed bootstrap plus only essential project boundary or safety constraints. Show the complete new file in the approval packet. Do not edit a broader ancestor instruction surface merely to bootstrap a narrower project. If the new local surface would be unowned, ineffective, or conflict with higher-precedence instructions, keep adoption passive.

Do not stack Thuban over an effective legacy rule that mandates a boot pair, one global current-state owner, or competing milestone maintenance. Before proposing any bootstrap diff, inspect the effective `AGENTS.md`; if one of those rules exists, a bootstrap-only insertion is invalid and the preview must show its exact replacement. Preserve and register useful legacy documents; never delete them automatically. Inspect nested instruction scopes. If the bootstrap's effectiveness cannot be established within the active chain, adoption is passive in that scope.

Minimal block:

```markdown
<!-- THUBAN:BOOTSTRAP v1 -->
For project work, read `THUBAN.md` first and follow only the routes relevant to the task. After verified, authorized work, follow its narrow Maintenance rule; invoke `$thuban` before changing governance.
<!-- /THUBAN:BOOTSTRAP -->
```

The matched start and end markers define the only managed range. Update one recognized block instead of adding another. Duplicated, unbalanced, or unknown-version markers are conflicts: do not guess a range; report them and preview an exact repair.

If the effective instruction surface cannot be updated, adoption is **passive**: the documents exist, but future tasks must invoke Thuban or read the root node explicitly. Report that limitation; do not claim persistent adoption.

## Lifecycle

Split a node only after a real boundary or repeated routing/state collision appears. Merge or retire one when that independent value disappears. Preserve useful history through existing version control or a deliberate archive; do not leave redirect stubs unless a live consumer needs them.

Audit in three layers:

1. **Structure:** markers, parents, paths, bootstrap, and route targets resolve.
2. **Semantics:** scope, authority, state ownership, and truth roles do not compete.
3. **Recovery:** a fresh agent can find the minimum evidence for a representative task without loading unrelated branches.

Audit and repair are separate authorities. A request to inspect does not authorize edits.

## Reporting postures

Use three consequence levels:

1. **Notify only:** read-only audit findings, uncertainty, and `zero diff`; do not ask for confirmation.
2. **One bundled confirmation:** related local governance changes with one verdict, exact write set, authority effect, and explicit exclusions. One approval covers only that packet; do not request serial approval for each file or equivalent step.
3. **Action-specific confirmation:** external writes, destructive disposition, new cost, or access and permission changes. Keep these separate from the local-governance packet and follow the stricter applicable boundary.

- An adoption preview's default write set is the required `THUBAN.md` node or nodes plus one managed `AGENTS.md` bootstrap. Register existing project documents in place. Report their stale state, verbosity, duplicate facts, or legacy read/update prose as separate drift unless the user's current request explicitly authorizes those exact repairs.
- Include another existing project document in the adoption diff only when it remains an effective competing instruction after the managed bootstrap and cannot be bounded by the node contract.
- Only an automatically effective instruction surface, such as an applicable nested `AGENTS.md`, qualifies for that exception. Ownership claims, read-first/update prose, status summaries, and methods inside routed project documents are evidence to bound in `Contract`, not adoption edits.
- **Preview:** verdict, scope, exact proposed files or diff, authority effects, approval needed.
- **Audit:** verdict, evidence, drift by consequence, uncertainty, recommended next action.
- **Completion:** changed files, decisions preserved, validation, remaining risk.
- **Maintenance:** changed truth and file, or `zero diff`.

These are shapes, not mandatory templates. Omit sections with no consequence.
