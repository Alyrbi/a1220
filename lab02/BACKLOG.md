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
- [F] B7: The technician needs to see an item's past loans when investigating repeated loss or damage.
- [NF] B8: After a service restart, all acknowledged loan and return records must still be present and unchanged.

## The change

After Tasks 1–4 were committed, I opened only `sealed/change-C-labloans.md`. The technician says most equipment disappears during exam weeks and requests a weekly report of every open loan because exams start soon.

B9 enters the backlog at priority 3, after recording loans (B1) and viewing outstanding loans (B2), which supply the report's data. B9 enters the three-item Sprint 1 and displaces B3 return tracking to the next increment. The sprint stays two weeks and three items. Its goal and checks now cover recording, viewing and reporting open loans; the existing manual register remains authoritative until return tracking and privacy/recovery gates are complete. The actual exam date is unknown, so the 6 November milestone must confirm it rather than promise that a proposed release date precedes exams.

## From the assistant

Kept:

No suggestions requested yet.

Rejected:

No suggestions requested yet.
