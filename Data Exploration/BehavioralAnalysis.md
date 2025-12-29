# Scenario: Behavioral analysis of user's sign-in activity

## Introduction
The goal with the scenario based approach is to enhance investigations and make retro-hunting repeatable, and fast by grounding Sentinel MCP data exploration with a concise, versioned context file that encodes scope, assumptions, and preferred analysis patterns. 

Behavioral analysis focuses on user sign-in activity (e.g., unusual IP diversity, geolocation changes, user agent anomalies, and IP reputation checks) using Microsoft Sentinel data lake via the [Sentinel MCP data exploration](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-data-exploration-tool) and [Triage tool collections](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-triage-tool).

These instructions are evaluated primarily in VS Code with Copilot + Sentinel MCP, but also work in other MCP-enabled AI tools that can leverage the same context, including Microsoft Foundry, Copilot Studio, Microsoft Security Copilot, and OpenAI ChatGPT.


## Expected Outputs
- Ranked users by distinct sign-in IP addresses.
- Geolocation anomalies (e.g., new or rare countries for a user).
- Suspicious user agent patterns or changes.
- IP reputation assessment summaries.
- Consolidated summary with mitigation and remediation recommendations.


## When to use?
- Behavioral Analysis Flow: Uses search_tables + query_lake to explore long-term data with KQL across UEBA-related tables like BehaviorAnalytics, Anomalies, AADUserRiskEvents, and UserPeerAnalytics. It’s analyst-driven, synchronous, and suited for broad hunts and trend discovery.
- Behavioral flow: Broad discovery, hypothesis testing, custom KQL, trend and population analytics.


## Scenario Flow & Instructions
The following section contains instructions for the MCP server. Copy and paste them into `context.md` and use with your preferred MCP client and an LLM to get the most out of it. 


## Behavioral analysis of user's sign-in activity – Instructions and investigation flow to use with Sentinel MCP server
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


## Sample Prompts
- "Find all users who have signed in from the most distinct IP addresses in the last 30 days"
- "Show me users with unusual geolocation changes in their sign-in patterns"
- "Identify users with suspicious user agent anomalies in their authentication activity"
- "Check IP reputation for all sign-in attempts from the top 5 users with most distinct IPs"
- "Analyze sign-in behavior for users and highlight any country-based anomalies"
- "Find users signing in from high-risk locations or IPs with bad reputation"


Figure 1: Behavioral analysis of an entity in VS Code using the Sentinel Data Exploration MCP tools. The investigation flow analyzes top 3 users with distinct IP address in the environment. In the demo environment in scope, only 1 user was found with distinct IP address.

<p align="center">
  <img src="../media/BehavioralAnalysis-6-0.png" alt="Check IP reputation for all sign-in attempts from the top 3 users with most distinct IPs" width="800" />
 </p>

Figure 2: Summary of IP reputation analysis.
<p align="center">
  <img src="../media/BehavioralAnalysis-6.png" alt="IP reputation analysis summary" width="800" />
 </p>

Figure 3: IP Address breakdown by success rate.
<p align="center">
  <img src="../media/BehavioralAnalysis-7.png" alt="Success rate breakdown" width="800" />
 </p>

 Figures 4 & 5: Application usage analysis & IP address security indicators.
 <p align="center">
  <img src="../media/BehavioralAnalysis-8.png" alt="" width="800" />
 </p>

 <p align="center">
  <img src="../media/BehavioralAnalysis-9.png" alt="" width="800" />
 </p>

Figure 6: Recommendations and summary statistics.
 <p align="center">
  <img src="../media/BehavioralAnalysis-10.png" alt="" width="800" />
 </p>

 References to find out more information:

- [Microsoft Sentinel MCP Server - Overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-overview)

- [Microsoft Sentinel MCP Server - Tool Collection](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-tools-overview)

- [Sentinel MCP data exploration collection](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-data-exploration-tool)