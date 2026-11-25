# Voltron / DEM Embedded SRE Context

**Purpose:** Portable, sanitized working context for another AI assistant.
**Last updated:** 2026-11-24

## Memory sync preference

Keep this handoff synchronized with the canonical local project memory and the README in the user's `ai-mem` repository. Sync after meaningful changes to scope, validated service understanding, stakeholder decisions, deliverables, or next steps, and do a weekly reconciliation while the engagement is active. A weekly in-thread sync check is scheduled for Friday at 5:00 PM local app time. Push only when content has changed, and merge remote edits rather than overwriting them. The destination repository is public, so preserve the export boundary: no internal URLs/hostnames, customer or organization identifiers, incident-specific identifiers, credentials, or sensitive operational details. If push access fails, leave the local copy updated and tell Vivek what needs to be fixed.

## Role and goal

I am an Embedded SRE learning and contributing with a dashboard/service team. My goal is to become useful through reliability work, improve operational readiness, and build enough service understanding to contribute effectively.

The agreed SRE activities are:

1. Participate in relevant on-call incidents during my business hours and time zone.
2. Learn the team's development process and where reliability reviews and changes belong.
3. Review the previous 12 months of incidents for cause and fix patterns.
4. Understand observability, alerts, and monitoring.
5. Build trust through regular collaboration with the service team.
6. Conduct a Failure Mode and Effects Analysis (FMEA).

The broader assignment is to understand the service, inventory and assess runbooks, identify gaps, recommend priorities, validate findings with engineers, and review findings with the service manager. Do not treat unassigned ideas as committed work.

## Current focused deliverable

The focused runbook for partial dashboard microapp route failures remains an existing draft pending team validation. A manager identified external-PR validation as a potential toil-reduction opportunity, and a related subtask is tracked. Kartikey's Nov 19 direction was to align candidate work with the Embedded SRE program. On Nov 20, Vivek chose a minimum viable PR change-record app integration in the target front-end repository, prioritizing a working integration over perfection and unrelated expansion. Desired behavior: the non-production environment should follow either a manual choice or the selected pipeline parameter. The DashX Jenkins PR pipeline has Commercial and China non-production parameters; the reference app reads provider-specific selections from PR-body checkboxes and does not consume pipeline parameters directly. The exact mapping from DashX deployment targets to the app's supported CHIM and ServiceNow environments remains to be established; China is not currently listed as supported. A local PR-template draft captures the gap. Keep this separate from the Actions-based PR validation work. Do not treat the runbook as approved or automation as validated until evidence supports it.

Kartikey also requested a week-by-week record. `WEEKLY_ACTIVITY_LOG.md` begins on the kickoff plan's Day One, October 5, and combines the kickoff assignment, dated manager emails, the team's weekly progress report, and a supplied chat export. It records October service updates from the team's report with inferred calendar-week mappings clearly marked; Oct 12–16 remains a historical activity gap. Calendar invitations are not treated as proof of attendance, and chat messages without timestamps are flagged for confirmation. Future entries capture focus, evidence, decisions, gaps, measured impact, and next steps. Remaining gaps should be filled from Vivek's records rather than inferred.

The weekly record maps the six core program activities and relevant operational-readiness/automation work to evidence and current status. It now has one source-linked weekly progress table with a Sam comment/validation field for every week, alongside the cross-week activity coverage matrix; repeated detailed week narratives were removed. Pending validation is not approval. The supplied DM and team progress report show runbook assessment and rollback-path work during the earlier weeks; DM messages have no timestamps, so some dates remain for confirmation. The reviewed manager emails add onboarding goals, meeting/stand-up invitations, a runbook update, a service-architecture discussion, and a positive but non-approving response. The focused runbook remains a draft; a qualitative FMEA for partial shell-to-microapp route failures is now drafted but is not complete or owner-reviewed. The formal 12-month incident review is not yet validated; no formal on-call rotation participation or toil-reduction measurement is recorded. PR validation and a new observability dashboard remain candidate secondary activities pending mutual selection and acceptance criteria.

Current state:

- The local draft has been revised and is awaiting service-team validation.
- The service manager described it positively (“great so far again”), but this is not approval, operational validation, or evidence that it has been exercised.
- The draft distinguishes confirmed information from hypotheses and explicitly marks unconfirmed SCC-specific actions and ownership.
- A recovery check currently described is for an affected user or approved representative to retry the exact failed route/action in every affected surface and record the outcome. The service owners still need to confirm whether further checks are required.

## Service understanding so far

- The dashboard shell hosts microapps, which can be independently built/deployed. A healthy shell or shell-level synthetic does not prove every microapp route works.
- Existing service material describes microapp assets as bundled and hosted in object storage. Organization settings and selected versions can affect what users see.
- BFG is associated with organization settings and version selection. Do not assume override inheritance, blast radius, restoration, or cleanup behavior without owner confirmation.
- Role and scope behavior may affect menus and routes. Meeting material distinguishes the user-provisioning mode from a separate RBAC feature flag; do not conflate them or treat meeting descriptions as current operational authority.
- SCC and standalone product surfaces can have different version controls and support paths. A support channel is known, but the current SCC UI/environment, authorized operator/approver, and exact procedure remain unconfirmed.
- The documented source rollback flow includes a source revert and deployment pipeline. A temporary version selection may be a faster mitigation, but current setting labels, approvals, cleanup, and recovery must be confirmed with owners.
- Environment and pipeline behavior can differ by commercial, government, and other deployment boundaries. Confirm the current component/version matrix rather than assuming parity.

## Work completed and recent learning

- Reviewed service and architecture documentation, deployment/on-call material, and relevant meeting recordings/notes.
- Created a focused route-failure runbook draft and a self-contained consolidated Voltron/DEM knowledge document covering the requested architecture, repository/pipeline/environment, deployment/rollback, runbook, monitoring/on-call, contacts, references/incident learning, and open-owner topics. A local service folder also contains supporting source notes, the standalone runbook, a coverage checklist, and an open-question tracker. All checklist areas remain partial pending current owner, environment, monitoring, or access confirmation. The team Git destination is still being identified, so the folder remains local staging.
- Inspected the deployment-guide screenshots and updated the route-failure runbook with the documented distinction between Release Please and manually triggered split deployments, plus the DashX form's change-ID field. The images do not confirm current approval policy, partial-failure rollback criteria, SCC procedure, or route-level recovery; those remain open.
- During a runbook discussion, an active tenant issue arose and an experienced engineer used it to demonstrate version rollback and verification. This improved operational understanding but did not constitute a tabletop or validate every runbook step.
- Reviewed a separate RBAC overview recording and a separate teammate discussion summary. Keep those sources distinct; the teammate document is an overview of a call, not a recording/transcript of that person.
- Identified an incident-review lead using dashboard/service search terms. Access guidance and monitoring links from a teammate are still pending.
- A resource manager asked that SCC/BFG questions be assigned to an owner and discussed in the team's regular stand-ups; until confirmation, mark them unconfirmed.

## Open questions

1. Who will own SCC and BFG procedure confirmation? Ask the service manager to name the appropriate owner.
2. What is the correct SCC UI/environment, and who approves/performs the change?
3. Which BFG setting name is current for the scoped environment, and who owns any temporary override cleanup if that becomes relevant?
4. Is exact-route user verification sufficient for recovery, or are additional checks required?
5. Which team Git repository should hold the one-folder service knowledge package?
6. Which repositories, Jenkins jobs, deployment environments, dashboards, alerts, and on-call contacts are current? Existing links and meeting reports need freshness checks.
7. Who is the team's chosen partner for a bounded incident review, and how should I obtain access/walkthrough for incident and monitoring tools?

## Next plan

1. Use the engineer's offer to map issue types to runbook actions and support shadowing; share the incident inventory and schedule a tabletop.
2. At the next Tuesday/Thursday stand-up, align the open owner questions and proposed work with the service manager. Keep unverified runbook steps marked as unconfirmed; do not call the runbook approved, tested, or complete without evidence.
3. Ask my resource manager for the designated Git repository, then place the complete service knowledge folder there using the team's normal review process.
4. Align the prior-year incident review with the teammate selected by the service manager and obtain the promised access/walkthrough.
5. Continue filling the service inventory with current evidence for architecture, repositories, pipelines, environments, deployment/version/rollback, runbooks, monitoring/on-call, contacts, documentation, incident learning, and open questions/owners.

## Additional context (synced from Claude project memory, 2026-11-16)

**Program shape:** about 2 months at roughly 75–85% time, with a one-month checkpoint with an SRE architect, an end checkpoint, then knowledge transition. The goal is toil reduction and reliability, not added dev capacity.

**Not assigned unless the service manager confirms:** day-0 onboarding work, government/federal promotion help, a security list the manager is compiling, a demo proxy, dashboards built from existing logging data, and a missing-region alert for monitoring agents.

**Commitments from the 12 Nov stand-up:** the service manager will give runbook feedback (herself or via the team) by Tue 17 Nov and identify a toil area for me.

**More service understanding (from docs and recordings; verify before operational use):**

- The dashboard service is treated as P0. It owns the dashboard experience, BFG, the design system/CSS layer, onboarding, and the microapp hosting framework (assets in object storage, served via CDN).
- A web entry point bootstraps the shell. SCC uses a separate remote-frame entry, which has module-federation differences. A manifest drives routes and menus, and RBAC affects menu and route generation.
- The network-experience side includes a UI microapp, a Go proxy service behind the API gateway/load balancer/containers, an AI assistant, and infrastructure running network-monitoring agents. Moving that infrastructure onto the dashboard platform is a work-in-progress proposal, not a decision.
- Environments include commercial, a regional sovereign deployment, and several government levels. App presence is not uniform across them. The SCC integration version setting affects all integration orgs.
- The evidence incident showed a detection gap: the shell loaded and shell-level synthetics did not fire, so the route failure was detected days later. It was mitigated by pinning an older version and rolling back.
- Known documentation conflicts to resolve with owners: proxy GA status, whether an auth migration is complete (its cutoff date has passed), and the rollout status of a security component.
- A past regional certificate-expiry outage led to auto-renewal being added.

**Working preference:** when I share meeting transcripts or dictation, categorise who said what and confirm attribution with me before updating notes.

## Execution plan alignment (synced 2026-11-17)

Source: the program's embedding execution plan document. It is sanitized here, with no names or links.

- **Program rules:** do all 6 core activities, plus at least 4 secondary activities agreed with the dev manager. Sign off a one-page charter covering the focus track, top 3 deliverables and explicit out-of-scope items. Program wrap-up is **1 Dec 2026**, where each embedded engineer proposes how they will share knowledge. The 1-month checkpoint was 3 Nov.
- **My pod's suggested focus:** service architecture, observability, runbooks. The closest program focus track is "Automated Recovery & Runbooks", in a lighter form.
- **Gaps as of 17 Nov:** no signed charter or activity selection; no on-call participation yet (the team is US-based); FMEA not started; incident review and observability inventory only partial; runbook awaiting validation.
- **Proposed selection (not yet agreed):** the core 6, plus outage/degradation-mode assessment, runbooks for recurring outage modes, actionable vs non-actionable alert classification, and service/infra ownership boundaries. Proposed out of scope: deploy-from-scratch, backlog fix, top-10 automated remediation.
- **Proposed top 3 deliverables:**
  1. Owner-reviewed, tabletop-walked route-failure runbook.
  2. Scoped FMEA of the shell → microapp delivery path, built from the 12-month incident review.
  3. Alert/observability inventory with classification and detection gaps.
- **Timeline:**
  - Week of 17 Nov: charter sign-off at stand-up, incident inventory, monitor inventory.
  - Week of 24 Nov: FMEA, alert classification, runbook tabletop. US holiday, so expect slow responses.
  - 1 Dec: wrap-up pack, knowledge-sharing proposal, proposed ownership area.
- **Confirmed 17 Nov:**
  - End date is 1 Dec; I may ask for an extension to 5 Dec.
  - The 1-month checkpoint never happened. Progress is tracked in a shared program sheet instead.
  - Access today: incident portal, CI (Jenkins), read-only cloud. Not yet: logging/search and paging.
  - Service manager runbook feedback still pending.
  - The intended SCC/BFG/recovery reviewer accepted a meeting just before the stand-up. Goal: get each runbook step marked confirmed / changed / other owner, plus a tabletop date.

## Incident review first pass (synced 2026-11-17, sanitized)

- **Scope:** 10 incidents in the last 12 months tagged to the dashboard/network-experience services. Severity: four significant, six low.
- **Provisional themes** (from titles only; to be confirmed from retros):
  - A. Partial UI failure after a change (shell loads, pages fail): 3 incidents. Supports the current runbook.
  - B. Dependency or auth failure (gateway/DB, monitoring vendor, token): 3 incidents. Candidate for the second runbook.
  - C. Certificate expiry: 1 incident, widest impact.
  - D. Data correctness / operational error: 3 incidents, likely owned by the backend team rather than the frontend service. This is an ownership-boundary question.
- **Next:**
  - Widen the search terms to check completeness.
  - Read the 5 available retros for detection source, time to detect/mitigate, fix and recurrence.
  - Confirm ownership per incident with the service team.

## Stand-up update (synced 2026-11-17 evening, sanitized)

- **Ownership:** most incidents on my first list belong to a different (backend dashboard) team.
  - The network-experience incidents belong to this team and already have well-regarded runbooks. My next step is to review those.
  - The service manager will return an edited list.
  - A senior engineer will confirm which earlier incidents belong to the frontend service. He still owes me runbook feedback.
- **Implication:** the team has only about 2–4 incidents in 12 months. The FMEA must be design-based, not only history-based. Forward-looking inputs:
  - an upcoming multi-account navigation/routing feature
  - a cross-origin allowlist change for a new embedding surface
  - a minor org-settings workaround
- **Deployment freeze until 5 Dec**, so the runbook can only be exercised through a tabletop before my end date.
- **Possible detection control:** a teammate added end-to-end tests covering all 6 microapps. To confirm: do they run after each deploy or only in CI?

## Live walkthrough and incident-inventory update (synced 2026-11-17, sanitized)

- A live tenant issue arose during a runbook discussion, and an experienced engineer walked through the resolution. The approach described was to select a known-good frame version, wait for propagation, verify the affected organization, and remove its override only after verification. Reverting to the last known-good release was described as the preferred rollback approach.
- Older frames may not support some custom telemetry events, which could fail silently; verify relevant behavior after changing versions. These are reported operational learnings, not a validated general procedure. Approval, exact setting/UI, propagation time, and applicability across product surfaces still require confirmation.
- The engineer offered to map issue types to runbook actions and support on-call shadowing. Ownership boundaries between the settings site and the dashboard frame service were clarified.
- The stand-up covered incident-inventory ownership; the service manager corrected the ownership assessment, and a tracking reference was shared. Preserve the updated ownership when continuing the incident review.
- Follow-up: share the incident inventory, review the team's existing runbooks, continue a design-based FMEA, and arrange shadowing/tabletop work. This walkthrough is not itself a tabletop or full runbook validation.

## Initial engagement framing (manager email dated 2026-10-06, sanitized)

- The manager's initial 1:1 invitation framed the embed around onboarding to the Day-0 activities and partnering across two related service teams to improve on-call and runbook hygiene.
- The manager's stated goals included improving runbooks and alerting, building dashboards from existing observability data, and reducing deployment burden, especially for government deployments. These are broad objectives, not separate assignments unless prioritized.
- The shared resource bundle covered on-call operations, deployment troubleshooting and validation, settings references, service architecture, alerts, and E2E testing. Some documents were explicitly marked work in progress; the Day-0 kickoff plan was later reviewed locally and is now the reference for core activities and mutually selected secondary activities.

## Manager 1:1 update (summary supplied 2026-11-19, sanitized)

- **Reported toil:** the weekly on-call engineer manually reviews external PRs as a deployment gatekeeper, checking required checklist items, test evidence, and approved change-ticket presence, with repeated follow-up when contributors omit items.
- **Near-term priority:** investigate a GitHub PR check/Action that surfaces missing requirements. The proposed first pass checks checklist completion, change-ticket presence/approval, and basic test evidence. Another team's existing validation flow was suggested as a template; exact implementation and policy are not yet verified.
- The manager said she would create a tracking subtask with the requirements and supporting runbook/docs. Vivek will discuss capacity with his resource manager before implementation. Dashboard aggregation is useful but was deprioritized for future tracking.
- Open details: exact checklist fields/evidence, ticket approval verification, informational vs blocking behavior, event/permission constraints, maintenance owner, and rollout/rollback. Review the ticket and referenced docs before coding; use the transcript only if those sources leave policy ambiguous.
- The manager also reportedly said some transferred services already have maintained runbooks/monitors while Voltron has gaps, and she would identify specific incidents needing runbook work. Keep the existing runbook scope and incident review, but align any expansion to those specific findings.

## PR validation reference review (2026-11-19, sanitized)

- The target repo's existing PR template asks for work-item/change-ticket fields, checklist completion, a testing description with environment selections, author certification, and a screenshot. This provides a starting point for content validation.
- The reference implementation separates (1) an Actions check for PR title/template/checklist/default text and (2) a release-targeted Actions check that verifies ticket-link presence and allowed URL formats. These checks comment on the PR, add labels, and set a workflow result. The ticket check does not call the ticket systems to establish approval state.
- A separate Probot/GitHub App responds to PR-comment commands. Its documented commands include dry-run, create, update, revoke, and status validation for change records. The sample PR shows it creating change records; that is distinct from the Actions validation results. App installation needs repository administration approval, and the sample does not prove status lookup is wired into a merge-blocking check.
- **Implementation direction (proposal):** first adapt deterministic template and ticket-link validation to the target repo's existing PR template. Treat actual approval-state checks as a separate integration requiring an approved source and explicit passing states. Test-evidence presence is not proof tests ran; confirm whether evidence links or existing CI signals are expected. Confirm branch/environment policy, blocking behavior, exceptions/bypass, and ownership before enforcing.
- The PR-validation work is now recorded as a high-priority subtask under the embedded-service readiness baseline, but remains in triage with no assignee or acceptance criteria in the reviewed snapshot. The parent task calls for one critical government-environment user-journey baseline: confirm scope, review existing E2E/CI and monitoring, assess deployment validation/runbook coverage, conduct a safe walkthrough/tabletop, and document evidence and follow-ups. It explicitly says to reuse existing tests and avoid duplicating work owned elsewhere.
- The linked on-call guide says the manual PR gate checks an approved reviewer, successful build/quality gate, adequate tests and test screenshots/video, linked change records, and—when targeting government environments—an approved ServiceNow ticket. Treat these as candidate requirements; the subtask must define which ones automation covers and for which branch/environment.

## Incident-process case study (updated 2026-11-24, sanitized)

- A resolved third-party cloud-region incident was reviewed as a learning case for incident declaration and internal-detection recording. The available case record identifies an internal browser/login synthetic as the detection source; the incident was formally created later. The time gap is a question for process review, not proof of a policy breach.
- The internal-discovery field was corrected after its meaning was discussed. This confirms how the case was classified, but the service-wide incident-opening trigger and current field guidance still need confirmation from the process owner. Reported confusion or missed fields have not been measured as a baseline.
- The case review identified inconsistent impact classification between the incident system and its Jira mirror. A concise ticket draft was prepared to capture the investigation and seek owner-confirmed guidance; a separate case-based runbook draft describes evidence capture, status updates, and recovery verification. These drafts do not reopen or repeat the resolved incident response, and no Jira issue, policy, alerting, or incident-form change has been made.
- The outage runbook was reorganized into a responder flow: detect, triage decision tree, declare when the approved trigger is met, mitigate, communicate, verify recovery, then resolve/close/review. The declaration threshold, escalation route, update cadence, and recovery criteria remain owner-validation items.
- The case-study portion of the manager's ask is addressed: the detection source has been identified and the process gap has been documented. The work is not complete as team guidance until the opening trigger and field semantics are validated and the resulting decision aid is recorded in the agreed location.

## FMEA progress (updated 2026-11-24, sanitized)

- A qualitative FMEA draft is available for partial dashboard/microapp route failures, using one confirmed pattern and one provisional comparison case. Failure-mode wording and technical mechanism still need service-engineer validation.
- Risk scales, scoring, treatment priorities/owners, and broader case-set validation are pending. A Jira ticket draft was prepared to complete and review the analysis; no ticket has been created. The current worksheet is a working draft and is not presented as a completed or approved FMEA.
- Review of the approved retrospective for the anchor route-failure case clarified that impact was configuration-dependent, existing internal checks missed the affected variants, and diagnosis correlated the affected cohort with a recent authorization/routing change. Recovery across separate surfaces and later rollback verification were recorded as distinct milestones. The document also flags incident splitting as added overhead, proposes broader end-to-end coverage/documentation/faster rollback, and contains unresolved metric/timeline definitions. Treat these as case-specific evidence and follow-up questions, not team-wide policy without owner validation.

## Published documentation and issue-link audit (2026-11-24, sanitized)

- Vivek supplied links to the service knowledge base, route-failure FMEA and runbook, incident runbook, and team/program weekly reports, plus their tracking issues. The current source records were checked; public memory intentionally omits internal URLs and issue/incident identifiers.
- The route-failure FMEA is a working draft with one unscored failure mode, unresolved evidence/reviewer questions, and a very wide worksheet that needs a more readable layout and linked evidence.
- The incident runbook exists in Confluence, but its published version needs synchronization with the newer local responder lifecycle and triage decision tree. Declaration, escalation, update cadence, and recovery criteria still need owner confirmation.
- The service KB and weekly reports contain older inventory/FMEA status. Refresh them against dated evidence; keep user-reported grouping separate from service-owner validation.
- Jira tracking links were checked. Some child issues still need links to their published documentation and clearer remaining acceptance/validation work. No external pages or issues were edited during the audit.

## Status check (synced 2026-11-25, sanitized)

- The current engagement context lists Dec 1 as the end date; a possible extension to Dec 5 is not confirmed. A US holiday on Nov 26–27 may slow owner responses, so open validation questions should be raised early.
- The structured incident-response runbook is now present in the local project files. Its published copy still needs synchronization; declaration, escalation, update cadence, and recovery criteria require owner confirmation.
- The partial route-failure FMEA is published as a working draft. Its worksheet remains wide, evidence links need improvement, and scoring and service-owner review are still open.
- The 12-month incident inventory is reported complete and broadly grouped, but source coverage and owner validation remain undocumented. The updated weekly activity log records work through Nov 24; separate daily journal notes after Nov 20 were not checked.
- PR-template fields were updated in a draft change, but app installation/access and the dry run remain unconfirmed. No merge enforcement or approval-state validation is claimed.

## Working cadence (synced from Claude project, 2026-11-24)

- A weekday morning planning routine (8:40 AM local time) carries unchecked to-dos and pending/blocked items from the previous daily journal note into a new dated note, then gives the top 3 tasks with expected outputs, stand-up asks on Tue/Thu, and days left until the 1 Dec wrap-up.
- It prioritizes work that moves the three proposed deliverables: the owner-reviewed route-failure runbook, the scoped FMEA built from the incident review, and the alert/observability inventory. It only reads notes and messages Vivek; it does not message others or change tickets, docs, or production.
- Daily journal notes are Vivek's reusable record of Embed SRE work; keep them updated with to-dos and outcomes.

## Guidance for future AI assistance

- Mentor me clearly and practically; explain unfamiliar SRE/service concepts without assuming I already know the internal shorthand.
- Separate confirmed facts, reported meeting claims, inferences, proposals, and unknowns.
- Do not invent architecture, commands, access, ownership, production behavior, approvals, or rollout status.
- Keep the immediate runbook scope specific to partial microapp route failures; do not overgeneralize from one incident.
- Do not claim work is approved, tested, complete, or impact-measured unless the evidence supports that claim.
- For active tasks, handhold one executable step at a time with concrete instructions; avoid unrelated rabbit holes. Once the agreed deliverable passes validation, report completion and stop offering follow-on steps unless asked.
- Do not send messages or alter tickets/configuration/production. Draft communications for me to send.
- Treat this note as sanitized context. It intentionally omits internal links, hostnames, customer/org identifiers, and incident-specific identifiers. Refresh time-sensitive details with the service team.
