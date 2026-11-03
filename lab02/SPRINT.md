# Sprint 1 — LabLoans

## Sprint Goal

By the end of Sprint 1, the technician can record a fictional equipment loan, find it in the outstanding list and record its return without losing track of who held the item.

Sprint dates: 9–20 November 2026 (two weeks). Planning dates are proposed future targets, not claims of completed delivery. Capacity is fixed at three selected items; new scope must replace an item or wait.

## Selected items

- B1: The technician needs to record a loan linking one inventory item to its borrower and agreed due date.
- B2: The technician needs to see every outstanding loan with the item, borrower and due date.
- B3: The technician needs to record a returned item so that its loan no longer appears as outstanding.

## Definition of Done

- [ ] A tester following the saved demonstration steps can record fictional item KIT-001 for borrower DEMO-01 due 20 November 2026, and the outstanding list shows that exact item, borrower and date once.
- [ ] A tester can record the return of KIT-001 and confirm it disappears from the outstanding list while a separately recorded KIT-002 loan remains.
- [ ] A repeat request to loan KIT-002 while it is already outstanding is rejected with a visible explanation and does not create a second active loan.
- [ ] A record missing the item, borrower or due date is rejected without changing the outstanding list; the observed checks are saved with the increment.
- [ ] The demonstration uses only fictional borrowers, contains no real contact details, and includes written steps for the technician to repeat every selected-item check.

This is a reviewable demonstration, not a production release. B4 privacy controls and B8 recovery checks must be completed before using real borrower data.
