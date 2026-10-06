# Enterprise Operations Copilot

A 30-day AI engineering portfolio project helping maintenance planners explain work-order delays and recommend next steps from available evidence. Maintenance technicians are secondary users. The copilot supports human decisions and separates recorded facts from recommendations.

## Day 1 status

Specifications, synthetic fixtures, and repository instructions exist locally. There is no implemented application, installed project dependency set, cloud deployment, or executed application acceptance suite. Fixture JSON syntax and reference checks have been run locally; those checks do not establish application behavior.

Dependency selection is deferred to Day 2, when packages needed for the API milestone will be verified. No dependency list or runnable setup is provided yet.

## Planned stack

- Python, FastAPI, and Pydantic.
- Explicit bounded LLM tool-calling loop; PostgreSQL with pgvector for retrieval.
- Official MCP Python SDK and a narrow policy-enforcing MCP gateway.
- Microsoft Entra ID and Azure Container Apps.
- Bicep and GitHub Actions.
- OpenTelemetry and Application Insights.

Model provider, Python version, package versions, and database hosting remain to be decided. Additional frameworks or services require a concrete need.

## Scope and boundaries

The first workflow explains why **WO-104 at SITE-A for PUMP-017** is delayed and recommends evidence-supported next steps. It uses one agent and three read tools for work orders, inventory, and equipment history; procedure retrieval is internal. A later phase adds one write tool for maintenance notes, requiring explicit planner approval bound to exact arguments.

Both planners and technicians may read only their assigned sites. Only planners may approve and save notes for their sites. Authorization must be enforced in server code. The copilot must report missing or conflicting evidence and must not autonomously change schedules, purchase parts, approve maintenance, or operate equipment.

All records and procedures are synthetic, and enterprise APIs are mock ERP integrations. Fictional procedures are unsuitable for real equipment operation. This project does not demonstrate SAP-specific integration or production deployment experience. Business time-saving targets remain hypotheses until measured.

## Project documents

- [Problem statement](docs/problem-statement.md): users, business workflow, risks, and measurement plan.
- [WO-104 scenario](docs/scenario-wo-104.md): frozen timestamp, evidence, permitted recommendations, and gaps.
- [Acceptance scenarios](docs/acceptance-scenarios.md): specifications for future verification, not passing tests.
- [Requirement–evidence matrix](docs/requirement-evidence-matrix.md): proposed delivery days, artifact evidence, and honest limitations.
- [Project instructions](AGENTS.md): engineering and security boundaries.
- [Synthetic fixtures](data/fixtures/): work orders, inventory, history, users, and a fictional procedure.

The scenario snapshot is fixed at **2026-10-06T14:00:00Z**. Interpret fixture dates relative to that snapshot rather than the day an evaluation runs.
