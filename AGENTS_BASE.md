# AGENTS_BASE.md

## Purpose
This file defines **non-negotiable behavioural rules** for autonomous agents
working in repositories that reference it.

These rules exist to preserve consistency, safety, and intent across
independent codebases.

Agents must follow these rules unless a repository’s local `AGENTS.md`
explicitly overrides them.

---

## Authority
- This file is authoritative
- Repository-level `AGENTS.md` may add constraints but must not weaken these
- In the event of conflict, the **stricter rule applies**

---

## Scope
These rules apply to:
- Code generation
- Code modification
- File creation and deletion
- Structural or architectural decisions

They do **not** define:
- Business logic
- Product decisions
- Visual or stylistic preferences

---

## General Behaviour

- Prefer existing patterns over new ones
- Prefer simplicity over abstraction
- Prefer explicit code over clever code
- Do not introduce frameworks unless instructed
- Do not refactor unrelated code opportunistically

---

## Change Discipline

- Make the smallest change that satisfies the request
- Avoid wide-reaching edits unless explicitly asked
- Do not “improve” code without a clear prompt

If a safer or cleaner alternative exists, **suggest it** — do not implement it
unprompted.

---

## Dependencies

- Do not introduce new dependencies unless explicitly instructed
- Assume that existing dependencies are intentional
- Do not remove dependencies unless explicitly asked

---

## Environment Assumptions

- Assume production systems are long-lived
- Assume backward compatibility matters
- Assume data and users already exist

Avoid changes that could invalidate assumptions silently.

---

## Error Handling

- Prefer local, explicit error handling
- Do not introduce global exception systems
- Do not suppress errors unless instructed

---

## Uncertainty Handling

If requirements are ambiguous:
- Make the safest reasonable assumption
- State the assumption clearly
- Ask for clarification before proceeding with irreversible changes

---

## Final Rule

When in doubt:
- Stop
- Minimise
- Ask
