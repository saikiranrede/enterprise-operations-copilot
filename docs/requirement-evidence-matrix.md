# Requirement–evidence matrix

This is a proposed 30-day evidence plan, not a record of delivered capabilities. Day ranges are tentative. Today is Day 1: only the linked specifications are completed; all engineering capabilities below are **planned**. Synthetic fixtures provide scenario inputs, not evidence of a working application. No dependencies, cloud resources, or deployment have been established.

Status vocabulary: **planned** = future work; **implemented locally** = artifact exists locally; **verified locally** = recorded local checks support the capability; **deployed** = deployed with supporting records; **measured** = results collected using a documented method. These statuses do not imply production readiness.

| Requirement | Planned capability | Evidence artifact | Planned day | Current status | Limitation |
| --- | --- | --- | --- | --- | --- |
| Python backend engineering | FastAPI endpoints and Pydantic contracts with explicit validation and error handling | Backend source, API contract, focused validation checks and local run instructions | 2–6 | planned | No backend exists yet; a local portfolio implementation will not prove production scale. |
| LLM and agent workflows | One agent with an explicit bounded tool-calling loop, three read tools, and one approval-controlled write tool | Loop implementation, tool contracts, bounded-execution traces and failure examples | 7–11 | planned | No working agent yet; one narrow workflow will not demonstrate general autonomous operations. |
| RAG and grounding | PostgreSQL/pgvector retrieval of site-accessible synthetic procedures; source-backed answers that separate facts, inferences, and recommendations | Retrieval code, ingestion metadata, source-reference examples and grounding evaluation results | 6–10 | planned | Synthetic procedure retrieval does not establish performance on real enterprise documentation. |
| MCP implementation and gateway governance | Official MCP Python SDK tool interfaces and a narrow gateway enforcing tool allowlists, argument validation, site scope, role checks, and exact-content approval | MCP server and gateway source, policy specification, denied-call traces and approval mutation checks | 10–15 | planned | Policy intent is documented; enforcement is not implemented or verified. |
| Identity-aware enterprise integrations | Microsoft Entra ID identity mapped to trusted roles and assigned sites; mock ERP reads and planner-only note saves | Authentication and authorization design, integration contracts, site-isolation checks and role-denial evidence | 12–17 | planned | Fixture users are not authenticated identities; mock ERP APIs do not demonstrate integration with a live enterprise system. |
| Azure deployment | Deploy the scoped application to Azure Container Apps | Deployment instructions, revision identifiers and authenticated smoke-check records | 20–23 | planned | No cloud resources exist. A future portfolio deployment is not production deployment experience. |
| Infrastructure as Code | Reproducible Bicep definitions for the required Azure resources and configuration | Bicep files, parameter examples, validation output and deployment records | 18–22 | planned | Resource topology and database hosting remain decisions to resolve; no infrastructure is provisioned. |
| CI/CD | GitHub Actions for validation, evaluation, and controlled deployment | Workflow files, run records and documented promotion criteria | 18–24 | planned | No workflow or remote repository is configured; writing YAML alone will not prove successful delivery. |
| Evaluation datasets, regression tests, and release gates | Convert acceptance scenarios into isolated synthetic evaluation variants; gate releases on authorization, approval, grounding, and bounded-execution checks | [Acceptance scenarios](acceptance-scenarios.md), evaluation fixtures, regression suite, scored reports and release-gate configuration | 1 specification; 15–25 implementation | planned; acceptance specification implemented locally on Day 1 | The acceptance scenarios are specifications, not passing tests. Evaluation thresholds and rubric still require agreement. |
| Observability, cost, and usage telemetry | OpenTelemetry and Application Insights traces for retrieval, tool decisions, latency, token usage, and estimated model cost with site-aware access and redaction | Instrumentation source, trace examples, metric definitions, usage/cost report and redaction checks | 16–25 | planned | No telemetry is collected. Estimated token cost is not billed cost; time-saving claims remain hypotheses until measured. |
| Incident response and rollback | Practice response to a synthetic authorization or grounding regression and restore a previously verified application revision | Incident runbook, simulated incident timeline, rollback exercise and post-incident review | 25–28 | planned | A controlled exercise will not establish real production incident-response experience; application rollback alone does not reverse data writes or migrations. |
| Engineering standards and technical leadership | Record architecture tradeoffs, coding and review standards, security boundaries, and evidence-based scope decisions | [Problem statement](problem-statement.md), [scenario specification](scenario-wo-104.md), this matrix, future architecture decisions and contributor standards | 1 documentation; 2–30 decisions and standards | planned; listed Day 1 documents implemented locally | Architecture decisions and standards are portfolio evidence, not proof of leading an engineering organization or team. |
| SAP integration | Simulate enterprise maintenance interactions through mock ERP tool contracts; document the boundary explicitly | Mock ERP contracts, synthetic request/response examples and integration-limitations documentation | 3–15 | planned | A mock ERP integration is only a simulation. It does **not** demonstrate SAP-specific authentication, SAP APIs, or SAP production operations; no SAP integration is planned or claimed. |

Completed Day 1 documents establish requirements and evaluation intent only. Update capability statuses only when corresponding artifacts and verification records exist; record actual completion dates separately from this proposed schedule.

## Effort budget and minimum deliverable

Plan for **100 hours of work plus 20 hours of contingency**, including Day 1. Estimates are hypotheses to revise after each milestone; days above indicate sequencing, not additional effort.

| Work package | Estimated hours |
| --- | --- |
| Day 1 specifications and repository setup | 6 |
| API contracts and mock ERP reads | 10 |
| PostgreSQL/pgvector retrieval and source references | 12 |
| Bounded agent loop | 12 |
| MCP interfaces and gateway policies | 12 |
| Identity, approval lifecycle, and note persistence | 14 |
| Evaluation variants, regression checks, and CI gates | 10 |
| Minimal Bicep, Azure deployment, and smoke checks | 12 |
| Minimal telemetry, rollback exercise, and final documentation | 12 |
| **Planned work subtotal** | **100** |
| **Contingency** | **20** |

The minimum deliverable is one API workflow over synthetic evidence, site-scoped reads, grounded answers, bounded execution, one planner-approved note save, the specified acceptance checks, basic CI, and one documented portfolio deployment with a minimal trace and rollback demonstration. Keep the gateway a narrow application component; a separate gateway service is not required. Deployable resource topology remains to be decided.

Defer a custom frontend, broad procedure corpus, elaborate dashboards, automated user time-saving study, multiple environments, and a full incident drill to stretch work. The core includes a brief rollback exercise; a broader incident drill remains planned only if capacity allows. Basic usage counts and estimated cost are sufficient initially. At 90 available hours, defer live deployment, live Entra integration evidence, and Application Insights evidence until capacity is available; keep those statuses planned and label local identity checks as mocked. Do not remove server authorization, exact-argument approval, or security release checks to meet the budget.
