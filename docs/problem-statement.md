# Enterprise Operations Copilot: Problem Statement

## 1. Business problem
Maintenance planners need to understand why a work order is delayed and decide what to do next. Relevant evidence is spread across work orders, inventory, equipment history, and maintenance procedures. The first workflow asks: **Why is WO-104 delayed, and what next steps does the available evidence support?** The copilot supports a human decision; it does not make or execute maintenance decisions.

## 2. Users and their tasks
- **Primary user — maintenance planner:** Investigate delays, review evidence and recommendations, and optionally approve and save a maintenance note.
- **Secondary user — maintenance technician:** Review delays, equipment history, and applicable procedures to inform work and communicate findings.
- Both roles may read records only for their assigned sites. Only a planner may approve and save a maintenance note, within their assigned sites.

## 3. Current manual workflow
The user opens the work order, checks parts availability, reviews equipment history, and finds relevant procedures. They reconcile statuses and gaps, consult colleagues when needed, decide on next steps, and manually document the explanation. This baseline requires validation.

## 4. Proposed AI-assisted workflow
The user asks about WO-104. The application verifies site access, retrieves relevant procedures, and uses three read tools to inspect the work order, inventory, and equipment history. The inventory tool also returns related, site-scoped purchase-order records; no fourth read tool is needed. It returns an evidence-backed explanation, clearly separating recorded facts from inferred causes and recommended next steps. It reports missing or conflicting evidence. In a later phase, it can draft a note; saving requires explicit approval by an authorized planner of the exact work order and note content.

## 5. Inputs and outputs
**Inputs:** User question, authenticated role and assigned sites, synthetic work-order and inventory records, synthetic equipment history, and synthetic maintenance procedures.

**Outputs:** Delay explanation with source references, recorded facts, qualified inferences, recommended next steps, and evidence gaps or conflicts. Later: a note draft and an authorized save confirmation.

## 6. Scope
**In scope:** One agent, three read tools, procedure retrieval, site-restricted evidence gathering, and human-reviewed recommendations for the WO-104 scenario. One approval-controlled write tool for maintenance notes is planned for a later phase. Day 1 covers specification and repository setup only.

**Out of scope:** Autonomous schedule changes, parts purchases, maintenance approvals, equipment operation, additional agents or tools, real enterprise data, and real ERP integrations. Integrations are mock ERP APIs; no SAP integration or production deployment experience is claimed.

## 7. Risks and controls
| Risk | Corresponding control |
| --- | --- |
| Unsupported explanations or unsafe recommendations | Cite evidence, label inferences and recommendations, and require human judgment; never authorize or operate equipment. |
| Missing, stale, or conflicting evidence | Report gaps, timestamps when available, and disagreements; recommend verification instead of inventing an answer. |
| Access to another site's records | Enforce assigned-site authorization in retrieval and every tool operation, including note saves. |
| Unauthorized or unintended note saves | Require planner role, site access, and explicit approval bound to exact content; edited drafts require fresh approval; bind approver and revision, expire approvals, and prevent duplicate saves. |
| Instructions embedded in retrieved content | Treat records and procedures as evidence, not instructions; enforce tool policies outside the model and bound execution. |

## 8. Success metrics and measurement
- **Evidence quality:** Check claims against cited sources; target zero unsupported facts in agreed scenarios.
- **Gap handling:** Use incomplete and conflicting fixtures; require all introduced, relevant gaps and conflicts to be reported.
- **Authorization and approval:** Test both roles, cross-site access, and approval states; require zero unauthorized reads or writes.
- **Decision usefulness:** Reviewers score clarity, traceability, and actionable steps against a rubric with a pre-agreed passing threshold.
- **Time saved:** Compare time to a reviewed explanation for equivalent manual and copilot scenarios. Targets remain hypotheses until measured; report sample size, quality, and results.

## 9. Explicit assumptions
All records and procedures are synthetic. WO-104 belongs to a defined synthetic site, and user site assignments are supplied by trusted identity or authorization data. Mock records have stable identifiers and enough evidence to evaluate delay explanations. Procedure applicability and access can be determined by site and equipment context. Procedure retrieval is internal to the application, not a fourth read tool. Workflow realism, evidence sufficiency, approval semantics, and evaluation thresholds still require validation.
