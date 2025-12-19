<!-- Template: Full | Version: 1.0.0 | Last Updated: 2025-12-18 | Maintainer: <name/team> -->
# context.md (Full Template – Scenario Context)

Use this template to give GitHub Copilot + Sentinel MCP consistent context to run a scenario. Keep secrets out of this file.

## Metadata
- Scenario: <Behavioral Analysis | Entity Analyzer | Graph Tools | Compromised User | Triage>
- Owner: <name/team>
- Last Updated: <YYYY-MM-DD>

## Objective
- One sentence describing the goal and expected outcome.

## Time Window
- <e.g., last 7 days>

## Entities of Interest
- <users, devices, IPs, hosts, resources>

## Data Sources
- Sign-in/auth: <table or API>
- Alerts/incidents: <table or API>
- Graph/relationships: <table or API>
- Endpoint/events: <table or API>
- Config (e.g., CA policies): <table or API>

## MCP Servers to Use
- Sentinel Data Exploration MCP
- Triage MCP (if applicable)
- Enterprise Config MCP (if applicable)

## Parameters
- time_window: <e.g., 7d>
- top_n: <e.g., 10>
- allowed_countries: <e.g., ["US", "FI"] or reference to baseline>
- ua_rarity_pct: <e.g., 5%>
- ip_risk_threshold: <e.g., High | Score >= 80>

## Deliverables
- Findings table: explicit columns per step (see Decision Rules)
- Markdown summary: key findings, severity, and rationale
- Mitigation and remediation plan: prioritized actions with owners and due dates

## Decision Rules
- Country anomaly: flag if sign-in country not in `allowed_countries` or country changes > 2 within `time_window`.
- User agent anomaly: flag UA strings below `ua_rarity_pct` usage or OS/Device mismatches relative to user/device baseline.
- IP reputation: flag IPs with `RiskScore >= ip_risk_threshold` or matching known bad indicators.

## Acceptance Criteria
- All steps in the workflow executed for `time_window` and `top_n` scope.
- Each flagged user/IP has evidence (query results, fields) and a stated reason per Decision Rules.
- A single consolidated findings table and a clear remediation plan are produced.

## Assumptions and Constraints
- Allowed countries/baseline source is defined (e.g., HR records, device inventory, policy docs).
- Data sources are accessible and named concretely in the section above.
- Credentials/secrets are provided via environment or keychain; none stored in this file.

---

## Workflow

### Behavioral analysis of user's sign-in activity – Use Sentinel Data Exploration MCP server
Retrieve users with distinct IP addresses
- When asked, start by retrieving all users who have the most distinct IP addresses using sign-in.
Check for country-based anomalies
- Next, check if the top 3 users have been signing in from a different country.
Inspect user agent anomalies
- Then, check for anomalies in the user agent settings used to sign in to devices to see if there is anything malicious.
Verify IP reputation
- Last, check the reputation of the IP addresses that were used to sign in for maliciousness.
Summarize and provide plans
- Summarize all steps taken in a way that helps readers understand. Also, add mitigation and remediation plans.
