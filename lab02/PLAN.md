# Plan — LabLoans

## Process choice

### How stable and binding are the requirements?

The request identifies lost equipment but does not define borrowers, loan periods, approvals or what counts as lost. These operational rules need confirmation, so a detailed fixed plan now would depend on guesses; privacy and accurate custody records remain constraints throughout.

### How quickly can real feedback arrive?

The lab technician can review a small borrowing-and-returning demonstration at the end of each two-week sprint. Availability for a 20-minute weekly check-in is a planning assumption to confirm before Sprint 1 begins, not a meeting that has already happened.

### What does failure cost?

A wrong custody record can leave expensive equipment unaccounted for, while disclosing borrower details harms privacy. Use fictional data in demonstrations and keep the current loan register as the operational record until the technician has checked a pilot; do not replace it with an unverified prototype.

### How many pieces must move together?

The initial scope connects item identity, borrower identity and one outstanding-loans list, all used by a small lab team. Inventory labels and borrower contact details must agree with existing records, but there is no confirmed requirement to integrate with other campus systems in the first sprint.

Verdict: Use short, two-week increments with technician feedback because key operational needs are uncertain and a small usable slice can be reviewed quickly; retain explicit privacy, reconciliation and pilot checks before any real rollout.

## Milestones

| Milestone | When | What is true then |
|---|---|---|
| Confirm the operating rules | 6 November 2026 | A written brief records borrower eligibility, loan periods, inventory identifiers, the exam start date and the technician's review availability, with unresolved assumptions listed. |
| Sprint 1 demonstration | 20 November 2026 | The three selected Sprint 1 items pass their saved checks using fictional data and a technician feedback note is attached. |
| Controlled pilot readiness | 4 December 2026 | Return tracking, staff-only access and restart recovery checks pass; ten fictional loans reconcile exactly with the demonstration register. |
| Pilot review and release decision | 18 December 2026 | The technician has reviewed the pilot's custody discrepancies and overdue-loan list, and a written accept/revise decision states whether the manual register can be retired. |

## Risks

| Risk | Likelihood | Mitigation |
|---|---|---|
| Inventory labels are duplicated or missing, linking a loan to the wrong physical item. | Medium | Audit 20 sample items with the technician before the first demo; record missing labels and require one unique inventory identifier per item. |
| The technician cannot provide timely feedback, leaving loan rules unverified. | Medium | Request a named backup reviewer and a weekly review slot before Sprint 1; keep unresolved rules explicit and limit the increment to fictional-data demonstrations until reviewed. |
| Real borrower details are exposed during an early demonstration. | Medium | Use fictional borrowers only; make staff-only access checks a pilot gate and review the demo data before sharing it. |
| A rollout loses acknowledged loans or disagrees with the existing register. | Low likelihood, high impact | Keep the current register authoritative during the pilot; reconcile ten records and test restart recovery before considering replacement. |
