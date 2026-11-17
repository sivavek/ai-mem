# Voltron / DEM Embedded SRE Context

**Purpose:** Portable, sanitized working context for another AI assistant.
**Last updated:** 2026-11-17

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

The immediate deliverable is a human-usable draft runbook for partial dashboard microapp route failures: the shell can load while one or more microapp routes or actions fail. The draft uses a past route/RBAC incident as evidence for one failure pattern; do not turn it into a generic playbook or assume all route failures share that cause.

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

1. At the next Tuesday/Thursday stand-up, ask the service manager to identify the SCC/BFG owner and confirm the open operational questions with that owner.
2. Keep unverified runbook steps explicitly marked as unconfirmed; do not call the runbook approved, tested, or complete without evidence.
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

## Guidance for future AI assistance

- Mentor me clearly and practically; explain unfamiliar SRE/service concepts without assuming I already know the internal shorthand.
- Separate confirmed facts, reported meeting claims, inferences, proposals, and unknowns.
- Do not invent architecture, commands, access, ownership, production behavior, approvals, or rollout status.
- Keep the immediate runbook scope specific to partial microapp route failures; do not overgeneralize from one incident.
- Do not claim work is approved, tested, complete, or impact-measured unless the evidence supports that claim.
- Do not send messages or alter tickets/configuration/production. Draft communications for me to send.
- Treat this note as sanitized context. It intentionally omits internal links, hostnames, customer/org identifiers, and incident-specific identifiers. Refresh time-sensitive details with the service team.
