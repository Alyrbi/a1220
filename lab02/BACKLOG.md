# Backlog — LabLoans

LabLoans helps the lab technician track who has each piece of equipment and when it should come back, so overdue or missing items can be followed up.

Working assumptions to validate with the technician: borrowers are students or staff, each physical item has an existing inventory label, and the technician records handovers. The brief does not yet define loan periods or what counts as lost.

## Items

- [F] B1: The technician needs to record a loan linking one inventory item to its borrower and agreed due date.
- [F] B2: The technician needs to see every outstanding loan with the item, borrower and due date.
- [F] B9: The technician needs a weekly report of every open loan, including its item, borrower and due date, to follow up equipment during exam weeks.
- [F] B3: The technician needs to record a returned item so that its loan no longer appears as outstanding.
- [NF] B4: Borrower contact details and loan records must be visible only to authorised lab staff, with unauthorised access denied.
- [F] B5: The technician needs to identify overdue loans so that borrowers can be contacted.
- [NF] B6: The outstanding-loans list must display within two seconds in at least 95 of 100 checks with 1,000 active loans on the lab's normal connection.
- [F] B10: The technician needs to mark an open loan as reported missing and record its follow-up status without removing the custody record. (assistant)
- [F] B7: The technician needs to see an item's past loans when investigating repeated loss or damage.
- [NF] B8: After a service restart, all acknowledged loan and return records must still be present and unchanged.

- [NF] B11: Staff must be able to record a loan and open the weekly report using only the keyboard, with visible focus at every interactive control. (assistant)

## The change

After Tasks 1–4 were committed, I opened only `sealed/change-C-labloans.md`. The technician says most equipment disappears during exam weeks and requests a weekly report of every open loan because exams start soon.

B9 enters the backlog at priority 3, after recording loans (B1) and viewing outstanding loans (B2), which supply the report's data. B9 enters the three-item Sprint 1 and displaces B3 return tracking to the next increment. The sprint stays two weeks and three items. Its goal and checks now cover recording, viewing and reporting open loans; the existing manual register remains authoritative until return tracking and privacy/recovery gates are complete. The actual exam date is unknown, so the 6 November milestone must confirm it rather than promise that a proposed release date precedes exams.

## From the assistant

The following five suggestions were drafted by Codex while completing this lab. This triage is an AI-assisted draft for the student to review; it does not claim an independent student review took place.

Prompt used for this exercise: "Suggest exactly five additional backlog items for LabLoans, a campus equipment-custody tracker. The client now needs a weekly report of every open loan during exam weeks. Existing needs cover recording loans, outstanding loans, returns, staff-only access, overdue loans, history, response time and restart recovery. Give one need per line, tagged [F] or [NF], with no technology choices. Do not change the fixed three-item first sprint."

Assistant draft:

- [F] The technician needs to mark an open loan as reported missing and record its follow-up status without removing the custody record.
- [NF] Staff must be able to record a loan and open the weekly report using only the keyboard, with visible focus at every interactive control.
- [F] Borrowers need to reserve equipment for future dates.
- [F] Borrowers need recommendations for equipment related to their current loan.
- [F] Borrowers need to rate the equipment they borrow.

Kept:

- Suggestion 1 becomes B10 after overdue follow-up and response-time needs: it directly supports investigation of missing equipment while preserving custody evidence. It is below Sprint 1's urgent reporting work.
- Suggestion 2 becomes B11 after recovery: keyboard access is a checkable quality need, but it does not displace the first sprint's three committed items.

Rejected:

- Suggestion 3 (reservations): useful for availability planning, but the client has not requested bookings and it does not address the immediate missing-equipment problem.
- Suggestion 4 (recommendations): discovery is outside the custody-tracking brief and adds unrelated scope.
- Suggestion 5 (ratings): subjective feedback does not establish who holds a missing item or help produce the urgent open-loan report.
