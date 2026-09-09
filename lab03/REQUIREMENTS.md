# CampusPulse requirements

Name or team: Ali Yaarobi

Date: 2026-09-09

Status: requirements draft for validation; stakeholder approval still pending.

Source IDs S1–S6 refer to page 2 of the Lab 3 handout. “Release boundary”
refers to the paragraph following S6. Proposed decisions are recorded in
Section 8 instead of being presented as stakeholder evidence.

## 1. Release scope

### In scope

- University sign-in and verified group identities for a browser-based pilot of 5,000 students and 200 groups before Orientation Week.
- Following groups and viewing their announcements and events on phones and with screen readers.
- Shared officer drafting, approved publication, and university-wide or members-only visibility.
- RSVP with private attendance by default, optional disclosure of one's own name, and place/time correction notices.
- Reporting, moderation, retained report evidence, decision records, and group appeals.
- Minimum necessary personal data, cancelled-event attendance deletion, and controls against spoofed badges and repeated identical announcements.

### Out of scope

- X-1 [Won't] Native mobile apps; this release is browser-based.
- X-2 [Won't] Direct messages.
- X-3 [Won't] External users; access requires university sign-in.
- X-4 [Won't] Payments.
- X-5 [Won't] Video hosting.
- X-6 [Won't] AI recommendations.

All six exclusions come from the release boundary in the handout.

## 2. User requirements

- UR-1 [Must] Students can follow groups and find their permitted announcements and events in one place. [Source: S1; release boundary]
- UR-2 [Must] Students can RSVP without their names becoming visible to other attendees unless they choose disclosure. [Source: S1, S5]
- UR-3 [Must] Group officers can collaborate on drafts while reserving publication for approved officers. [Source: S2]
- UR-4 [Must] Groups can limit content to their members or share it across the university. [Source: S2]
- UR-5 [Must] Students who RSVP can learn when an event's place or time changes. [Source: S2]
- UR-6 [Must] Moderators can assess reports, hide content, and explain decisions using retained evidence when a group appeals. [Source: S3]
- UR-7 [Must] Student Affairs can distinguish checked groups with an official badge for the 5,000-student, 200-group pilot. [Source: S4]
- UR-8 [Must] The Data Protection Officer can require minimal personal data and deletion of cancelled-event attendance within 30 days. [Source: S5]
- UR-9 [Must] Students can use the essential event, follow, and RSVP journeys on a phone and with a screen reader. [Source: S1]
- UR-10 [Must] Students are protected by controls against false official-group claims and repeated announcements from compromised accounts. [Source: S6, S4]

## 3. Functional requirements

System requirements are developed in Task 3.

## 4. Non-functional requirements

Quality requirements are developed in Task 3.

## 5. User stories and acceptance criteria

Stories are developed in Task 4.

## 6. MoSCoW summary

Priorities are developed in Task 4.

## 7. Traceability

Traceability is developed in Task 4.

## 8. Assumptions and open questions

### Assumptions

- A1: University-wide means authenticated university users, not the public internet. Group membership and officer approval are distinct permissions; following a group does not grant membership.

### Open questions

- Q1: Who supplies authoritative membership records and approves officers? Confirm with S2 and S4; university sign-in alone does not establish either permission.
- Q2: What is the actual Orientation launch date and expected peak concurrency? The 5,000 students are pilot population, not a stated simultaneous-user load.
