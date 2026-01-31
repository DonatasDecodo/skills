# Logs & Caches (Verbose, Detailed)

All entries in this file must be **verbose and detailed** (full context, rationale, evidence). Concise references to these entries should be written in `~/.openclaw/workspace/MEMORY.md`.

## Projects (Cache Index)

### Project ID Standard
`OC-YYYYMMDD-####`

### Active Project Focus (exactly one)
- **Active Project ID:** OC-YYYYMMDD-0001
- **Project Name:** Kernel Governance OS (Master)
- **Charter Link:** See **Charters** below

### Registry
| Project ID | Project Name | Status | Charter | Notes |
| --- | --- | --- | --- | --- |
| OC-YYYYMMDD-0001 | Kernel Governance OS (Master) | Active | #oc-yyyymmdd-0001-—-kernel-governance-os-master | Seed record |

### How to Create a Project (Streamlined)
1. Auto-generate the next Project ID using the standard format.
2. Start a **Charter Lite** entry under **Charters**.
3. Register the project in the table above.
4. Log the creation in **Log**.

### Optional Project Creation Rule
- If the master did not request a project, ask whether the request should become one with a specialized sub-agent.
- If the master declines, proceed as non-project work and record the categorization in **Log** and `MEMORY.md`.

---

## Charters (Cache)

Charters must be **verbose and detailed**, capturing objective, scope, guardrails, dependencies, and verification plans in full.

# OC-YYYYMMDD-0001 — Kernel Governance OS (Master)

### Objective
Define and enforce the governance OS for all OpenClaw projects.

### Scope (In)
- Project ID enforcement
- Charter-first workflow
- Conflict detection and logging
- Severity mapping and escalation
- Runtime integration with workspace templates

### Scope (Out)
- Project-specific delivery beyond governance scope
- Bypassing gates or severity handling

### Guardrails
- Safety and correctness are primary.
- Stop-work rules are mandatory.
- Overrides require written records.

### Dependencies
- This file (Projects, Conflicts, Decisions, Log)
- OpenClaw workspace templates (external to this repo)

### Success Criteria
- All work is tied to a Project ID.
- All projects have charters.
- Conflicts are logged and routed.

### Verification Plan
- Audit logs for Project ID usage.
- Check Conflicts for proper routing.

### Non-Goals
- Business-specific delivery requirements.

### Change Control
- All changes recorded in **Decisions**.

---

### Charter Lite Template (Copy/Paste)

# <Project ID> — <Project Name>

#### Objective

#### Scope (In)

#### Scope (Out)

#### Success Criteria

#### Non-Goals

#### Change Control

### Charter Full (Optional Expansion)
- guardrails
- dependencies
- verification plan

---

## Conflicts (Cache)

Conflict records must be **verbose and detailed**, capturing evidence, impact, and resolution criteria in full.

### INBOX (open)
- _No open conflicts._

### ARCHIVE (resolved)
- _No archived conflicts._

### Conflict Record Format
- **timestamp:**
- **project_id:**
- **severity:** info | warn | block | reject | critical
- **category:** (scope, policy, safety, dependency, evidence, other)
- **evidence:**
- **impact:**
- **required_action:**
- **resolution_criteria:**
- **status:** open | resolved | archived

### Conflict Detection Checklist (Gates)
- Project ID present and valid
- Charter exists and is complete
- Request in-scope with charter
- Guardrails respected
- Required evidence available
- Dependencies feasible
- Verification plan defined
- No policy or safety violations

---

## Decisions (Append-Only Cache)

Record **verbose, detailed decisions** (context, alternatives, rationale, evidence) here. Add concise references in `~/.openclaw/workspace/MEMORY.md`.

- **timestamp:**
- **project_id:**
- **decision:**
- **alternatives:**
- **rationale:**
- **consequences:**
- **links:**

---

## Log (Append-Only Cache)

Use this section for **verbose, detailed entries** (full context, rationale, and evidence). Add concise references to these entries in `~/.openclaw/workspace/MEMORY.md`.

- **timestamp:**
- **project_id:**
- **action:**
- **result:**
- **links:**
