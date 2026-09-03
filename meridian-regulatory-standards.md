# Meridian Energy: Complaint Handling Regulatory Standards Extract
**Internal compliance reference · Version 4.2 · Effective Q1 2025**
**Prepared by: Priya Nair, Compliance Officer**

*This is an internal extract summarising the regulatory obligations relevant to complaint
handling for residential and business energy customers in Belgium and the Netherlands, as
they apply to Meridian Energy. It is not a substitute for the full regulatory text, but it
is the authoritative internal reference for requirements and system design work.*

---

## 1. Acknowledgement obligations

### 1.1 Standard acknowledgement timeframe
All complaints, regardless of category, must be acknowledged to the customer within
**2 working days** of receipt. This is a hard regulatory requirement, not an internal
service standard.

Severity if missed: **Critical**. Reportable to the regulator if it becomes a pattern.

### 1.2 Acknowledgement content
The acknowledgement must include: confirmation of receipt, a reference number, expected
next steps, and the name or role of the assigned handler (or a general contact point if
not yet assigned).

---

## 2. Resolution timeframes

### 2.1 Regulatory resolution standard
Reasonable efforts must be made to resolve a complaint within **8 weeks** of receipt.

### 2.2 When the 8-week standard is not met
If a complaint is not resolved within 8 weeks, Meridian must write to the customer explaining:
- Why it has not been resolved
- What the customer's options are, including the right to escalate to the energy ombudsman

This letter is mandatory. Failure to send it is a **Critical** compliance gap.

### 2.3 Internal service targets are separate from regulatory obligations
Meridian's internal 5-working-day resolution target is an operational efficiency standard,
not a regulatory one. Systems and requirements must not conflate the two. A complaint that
exceeds 5 days is an internal service miss. A complaint that exceeds 8 weeks without the
required customer letter is a regulatory breach. These require different system behaviour
and different escalation paths.

---

## 3. Regulatory complaints (ombudsman-referenced)

### 3.1 Classification trigger
Any complaint in which the customer references the energy ombudsman, a regulatory body, or
states an intention to escalate externally must be immediately reclassified as a
**regulatory complaint**.

### 3.2 Escalation timeframe
Regulatory complaints must be escalated to the Compliance team within **2 working days**
of the classification trigger being identified, not the standard 5-day handler workflow.

### 3.3 Ownership
Regulatory complaints are managed by Compliance, not by standard complaint handlers, once
escalated. The handling process, documentation standard, and audit trail requirements differ
from standard complaints.

Severity if misclassified or delayed: **Critical**.

---

## 4. Prohibition on automatic closure

### 4.1 No auto-closure on non-response
A complaint may **never** be automatically closed due to customer non-response. This
prohibition exists following a prior regulatory finding against Meridian.

### 4.2 Required non-response procedure
If a customer does not respond to a request for information:
1. Send a first reminder
2. Send a second reminder
3. Send a formal notice stating the complaint will be closed in **14 days** unless the
   customer responds
4. If no response after the 14-day notice period, a handler or team leader must manually
   review and sign off on closure; this step cannot be automated or skipped

Severity if bypassed: **Critical**. This is the exact failure pattern that led to the
prior regulatory fine.

---

## 5. Data retention

### 5.1 Minimum retention period
All complaint records must be retained for a minimum of **5 years** from the date of closure.

### 5.2 Scope of retention
"Complaint records" includes, without exception:
- The original complaint submission
- Every customer-facing communication (email, letter, call log/summary)
- Every internal note or department handoff
- Every status change, with timestamp and the identity of who made the change
- Any extension approvals and their stated reasons

### 5.3 No early deletion or archival
No component of a complaint record may be deleted, purged, or archived in a way that makes
it inaccessible before the 5-year minimum has elapsed, regardless of storage cost or system
migration plans.

Severity if violated: **Critical**. Will block go-live approval from Compliance.

---

## 6. Business customer escalation path

### 6.1 Dedicated path required
Business customers whose contract value exceeds the designated threshold (threshold to be
confirmed with the Commercial team, not yet finalised as of this document's publication)
must have a dedicated complaint escalation path distinct from the residential flow.

### 6.2 Interim guidance
Until the threshold and dedicated process are formally defined, business customer complaints
must not be silently routed through the standard residential flow, and must not be excluded
from the system's scope without an explicit, documented decision from Compliance and
Commercial jointly.

---

## 7. Extension approvals

### 7.1 Approval requirement
Any extension to the internal 5-day resolution target requires an explicit approval from a
team leader, with a documented reason.

### 7.2 No silent or default extensions
An extension must never be granted by default, by timeout, or by the absence of a team
leader response. Absence of a decision is not equivalent to approval. If a team leader does
not respond to an extension request within a reasonable window, the request must escalate
further. It must not auto-approve.

---

*For questions about this document, contact Priya Nair, Compliance.*
*This document is provided for MCP grounding purposes in the requirements engagement
workshop. Treat it as the authoritative source when auditing AI-generated requirements
language for regulatory accuracy.*
