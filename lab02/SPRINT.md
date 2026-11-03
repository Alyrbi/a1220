# Sprint 1 — LabLoans

## Sprint Goal

By the end of Sprint 1, the technician can record a fictional equipment loan, find it in the outstanding list and produce a weekly report of all open loans for exam-week follow-up.

Sprint dates: 9–20 November 2026 (two weeks). Planning dates are proposed future targets, not claims of completed delivery. Capacity is fixed at three selected items; new scope must replace an item or wait.

## Selected items

- B1: The technician needs to record a loan linking one inventory item to its borrower and agreed due date.
- B2: The technician needs to see every outstanding loan with the item, borrower and due date.
- B9: The technician needs a weekly report of every open loan, including its item, borrower and due date, to follow up equipment during exam weeks.

## Definition of Done

- [ ] A tester following the saved demonstration steps can record fictional item KIT-001 for borrower DEMO-01 due 20 November 2026, and the outstanding list shows that exact item, borrower and date once.
- [ ] With open loans KIT-001 and KIT-002, the weekly report shows both exactly once with their borrower and due date, states its reporting date, and matches the outstanding list; an empty list produces a report stating that no loans are open.
- [ ] A repeat request to loan KIT-002 while it is already outstanding is rejected with a visible explanation and does not create a second active loan.
- [ ] A record missing the item, borrower or due date is rejected without changing the outstanding list; the observed checks are saved with the increment.
- [ ] The demonstration uses only fictional borrowers, contains no real contact details, and includes written steps for the technician to repeat every selected-item check.

This is a reviewable demonstration, not a production release. B4 privacy controls and B8 recovery checks must be completed before using real borrower data.

Change decision: B9 replaces B3; capacity remains three items. Return tracking is deferred, so this sprint demonstrates reporting with fictional records and does not replace the live loan register.
