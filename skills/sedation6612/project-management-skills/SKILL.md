---
name: project-management-skills
description: A governed project management OS for OpenClaw that applies to master prompts, supports optional project creation with sub-agents, and emphasizes memory-first continuity.
---

# Project Management Skills

## Trigger Conditions
Use this skill whenever:
- The request comes from the **master** and involves project work, planning, delivery, or changes that can impact scope, safety, or governance.
- The master asks to create or manage a project, or to evaluate whether a request should become a project.
- Conflicts, uncertainty, or policy violations are possible.
- You must coordinate memory/continuity across sessions.
- **Do not** apply this skill to proactive work the agent initiates; that work should proceed and be categorized afterward.

## Quickstart Checklist
1. Capture the request and **infer missing fields** from prior conversation context (only when evidence is clear).
2. Ask the master if this should become a **project** with a specialized sub-agent presiding.
3. If yes, auto-create a **Project ID** and start a **Charter Lite** in `LOG_CACHES.md` under **Charters**.
4. Load caches: `LOG_CACHES.md`.
5. Run the **Conflict Detection Checklist**.
6. Proceed only if gates pass; otherwise log conflict and stop.
7. Execute the governed workflow in `INFO_GOVERNANCE.md` under **Governed Workflow**.
8. Log outcomes in `LOG_CACHES.md` under **Log**, decisions in **Decisions**.
9. Update runtime workspace files per `INFO_RUNTIME.md`.

## The 9 Setup Commandments (Stop-Work Rules)
**C1 Lock project isolation:** every unit of work belongs to exactly one Project ID **or** is explicitly logged as non-project work.
**C2 Master Project as OS/kernel governs all projects.**
**C3 Charter first:** no charter, no work.
**C4 Project optionality:** if the master did not request a project, ask whether this should become one; proceed without a Project ID only if the master declines, then log as non-project work.
**C5 Conflict detection:** run gates; conflicts can block.
**C6 Conflicts become logs:** every conflict is recorded.
**C7 Conflicts routed to messenger:** provide manual copy/paste payload.
**C8 Severity defined up front:** info, warn, block, reject, critical.
**C9 Kill fast-but-wrong:** if uncertain, add checks or record unknowns—never guess.

## Core References
- Governance rules: [INFO_GOVERNANCE.md](INFO_GOVERNANCE.md)
- Runtime integration: [INFO_RUNTIME.md](INFO_RUNTIME.md)
- Research notes: [INFO_RESEARCH.md](INFO_RESEARCH.md)

## Safety & Trust Warning
Safety and correctness override speed. If uncertain, **stop**, document unknowns, and escalate or request clarification rather than guessing.
