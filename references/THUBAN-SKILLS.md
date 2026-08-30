<!-- THUBAN:SKILL-ROUTER v1 -->

# Thuban Skill routing

Create `THUBAN-SKILLS.md` only when project work repeatedly pays a real cost choosing among Skills, or when the user explicitly wants a project capability router. It is not an installed-Skill inventory and not a package manager.

## Discovery without installation reports

Codex discovers Skills independently of this router. Whenever Thuban adopts, audits, or repairs a project, inspect the Skill names and descriptions discoverable in the current session against recurring project needs already supported by evidence. Do not require the user to announce a newly installed Skill, and do not treat the current session's catalog as proof that every installed Skill was enumerated.

Discovery is opportunistic, not a background subscription:

- an unrelated Skill produces zero diff;
- a relevant new Skill is at most a Candidate until representative project work supplies evidence;
- a Skill that materially succeeds or fails on recurring project work is capability evidence for the next governance review, not silent authority to rewrite the router;
- if no project router exists and repeated selection cost is absent, discovery alone does not create one.

## Project file

```markdown
<!-- THUBAN:SKILLS v1 -->

# Thuban — Skills

## Defaults
| Need | Skill | Use when | Evidence |
|---|---|---|---|

## Candidates
| Need | Skill | Test when | Unknown |
|---|---|---|---|

## Avoid
| Need | Skill | Avoid when | Evidence / alternative |
|---|---|---|---|
```

Omit empty sections. Use exact installed names so agents can route reliably. A Default must resolve to one uniquely invocable Skill; an unresolved same-name collision cannot be Default.

## Meaning

- **Default:** demonstrated fit for a recurring project need; this is the normal route under the stated condition, not universal permission to invoke it.
- **Candidate:** potentially useful, with a concrete project scenario that would test the unresolved question.
- **Avoid:** a known mismatch under stated conditions, with evidence and an alternative when available. It is not a permanent blacklist.

Route capability decisions, not popularity. Do not add every installed Skill, duplicate its manual, or promote a candidate because its description sounds relevant.

## Change events

Reconsider the router only when evidence changes a project capability decision:

- a recurring need appears or disappears;
- a Skill succeeds or fails on representative project work;
- compatibility, maintenance, cost, authority, or safety changes;
- two Skills repeatedly collide;
- the user asks for review.

Installing an unrelated Skill produces zero diff. Discovering a relevant installed Skill makes it a candidate at most until project evidence justifies another status. A missing Default or duplicate name is runtime drift: report it and preview installation, renaming, or routing alternatives, but do not silently rewrite project preference.

Keep one root router by default. Put domain-specific routing in a local node only when that scope has genuinely different needs; do not create a second pool merely because a local node exists.

Changing Defaults, Candidates, Avoid, or routing conditions is a governance decision. Preview it and obtain approval unless the user's current request explicitly authorizes that exact change.
