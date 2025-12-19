# Sentinel-MCP-Tools

Sentinel MCP Tools is a guideline for a collection of Microsoft Sentinel Model Context Protocol (MCP) tools designed to enhance automation, enrichment, and investigation workflows.  The goal of this repository is to provide modular, easy-to-extend instructions how to use Sentinel MCP tool collections that can be integrated into AI agents, or custom SOC automation frameworks.

In most of the examples Vs Code is used as MCP client but the scenarios works in other frameworks and MCP clients as well.

## Context.md
Use `context.md` to give GitHub Copilot + Sentinel MCP server a small, consistent brief for this scenario in VS Code. It keeps the assistant and tools aligned on scope, time window, entities, data sources, and preferred steps—so the same investigation runs the same way each time.

- What it is: a lightweight, non-sensitive scenario brief (no secrets).
- Where to keep it: in your workspace (e.g., `Data Exploration/context.md`) or use the repo template at `templates/context.template.md` and tailor it per run.
- How to use it in VS Code: if context.md is in the opened workspace, Copilot/MCP picks it up automatically; if it’s elsewhere, upload/attach it in Copilot Chat (or paste the relevant sections).
- What to include: objective, time window, entities of interest, key data sources/tables, and the workflow steps below.
- Secrets: store credentials in environment variables or your keychain—do not place tokens in `context.md`.


## Benefits

 **Consistency & Tool-Aware Guidance**:
 - Shared scope, terms, and steps keep MCP responses aligned.

 **Reproducibility & Auditability**:
 - Versioned context yields repeatable runs and clear review trails.

 **Determinism**:
 - Reduces variance across prompts and analysts for stable outcomes.

 **Speed & Focus**:
 - Cuts setup time by front-loading scope, filters, and preferred queries.

 **Secret Hygiene**:
 - Non-sensitive file; keep credentials in env vars or keychain.

 **Modularity & Onboarding**:
 - Small per-scenario files scale well and ramp new analysts faster.


## How to Use Context.md
1. Prepare a scenario-specific `context.md` for behavioral analysis (data source names, important fields, filters, definitions, risk cues, and preferred query templates).
2. Start the Sentinel Data Exploration MCP server for your profile/session.
3. In Copilot Chat (with MCP enabled), attach or reference your `context.md` so the assistant and tools share the same framing. If attachment is unavailable, paste the relevant sections.
4. Run the workflow below. Iterate by refining `context.md` or adding follow-up prompts as insights emerge.
5. Capture findings and decisions for handoffs and post-incident reviews.

## Prerequisites
- VS Code with GitHub Copilot and MCP client enabled for this profile.
- Access to your Microsoft Sentinel workspace and sign-in/identity telemetry.
- Sentinel Data Lake enabled and configured.
- Sentinel MCP server installed and accessible locally/remote. Means practically local MCP client configuration (e.g., `mcp.json`) pointing to your server.