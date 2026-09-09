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

- FR-1 [Must] The system shall require successful university sign-in before granting access to community content. [Source: UR-1, UR-7]
- FR-2 [Must] The system shall let a signed-in student follow or unfollow a group. [Source: UR-1]
- FR-3 [Must] The system shall show published, non-hidden announcements and events from followed groups that the student is permitted to view. [Source: UR-1, UR-4]
- FR-4 [Must] The system shall let approved officers of the same group create and edit a shared announcement or event draft. [Source: UR-3]
- FR-5 [Must] The system shall reject publication by anyone who is not currently an approved officer of the content's group. [Source: UR-3, UR-10]
- FR-6 [Must] The system shall restrict members-only content to current group members, including access through a direct link; following alone shall not grant access. [Source: UR-4]
- FR-7 [Must] The system shall let an eligible student create or withdraw one RSVP per visible, non-cancelled event and show that student's current RSVP state. [Source: UR-2]
- FR-8 [Must] The system shall omit each attendee's identity from attendee-facing lists by default and show that identity only after the attendee explicitly opts in for that event; opting out shall remove it again. [Source: UR-2, UR-8]
- FR-9 [Must] The system shall create an in-service correction notice showing the previous and new place or time for each current RSVP holder still entitled to view the event when an approved officer saves a published event's changed place or time. [Source: UR-5, UR-4]
- FR-10 [Must] The system shall delete attendance data after an event is cancelled. [Source: UR-8]
- FR-11 [Must] The system shall let a user report content they can view, recording a snapshot of that content and a non-empty report reason. [Source: UR-6, UR-10]
- FR-12 [Must] The system shall let a moderator hide reported content from ordinary views and direct links while retaining its report snapshot and reason in moderator-only evidence. [Source: UR-6]
- FR-13 [Must] The system shall record the moderator's identity, content ID, action, timestamp, and reason for each hide, restore, or appeal decision. [Source: UR-6]
- FR-14 [Must] The system shall let an approved officer of the affected group submit an appeal linked to its moderation decision and view the outcome without access to moderator-only evidence or reporter identity. [Source: UR-6, UR-3]
- FR-15 [Must] The system shall let Student Affairs record a completed group check or revoke that verification, displaying an official badge only while that group has an active verification record. [Source: UR-7, UR-10]
- FR-16 [Must] The system shall reject attempts by group officers or ordinary users to assign or modify the official verification state. [Source: UR-7, UR-10]
- FR-17 [Must] The system shall reject a repeated publication of identical announcement text and links by the same group within 60 seconds of its last successful identical publication, with no additional feed item created. [Source: UR-10; assumption: A4]
- FR-18 [Must] The system shall collect only the approved field inventory in A5 and reject additional personal-profile fields. [Source: UR-8]
- FR-19 [Must] The system shall let an approved officer cancel their group's event, preventing new RSVPs and removing it from upcoming-event views. [Source: UR-8, UR-3]
- FR-20 [Should] The system shall let an approved officer preview a draft as it would appear to an eligible attendee before publishing it. [Source: UR-3; assumption: A6]
- FR-21 [Could] The system shall let a student sort their permitted upcoming followed-group events by ascending start time. [Source: UR-1; assumption: A6]

## 4. Non-functional requirements

- NFR-1 [Must] The system shall support the stated pilot population. [Measure: with 5,000 distinct student accounts and 200 groups loaded, sign-in, follow, publish, and RSVP scenario checks complete without a population-limit rejection or missing saved record; this is a sequential capacity check, not a concurrency claim.] [Source: UR-7; S4 supplies the population figures]
- NFR-2 [Must] The system shall make the essential journeys usable on phones and with screen readers. [Measure: all steps for finding an event, following a group, making an RSVP, and changing name visibility can be completed at a 360-CSS-pixel viewport without horizontal page scrolling, and using keyboard navigation with VoiceOver/Safari; every control exposes a meaningful name, role, and state.] [Source: UR-9; assumption: A2]
- NFR-3 [Should] The system shall respond promptly to feed requests under the provisional pilot workload. [Measure: p95 server response time at most 2 seconds and fewer than 1% failed feed requests during a 10-minute staging run with 100 simultaneous signed-in users, each requesting the feed every 5 seconds, using the NFR-1 population dataset.] [Source: UR-1, UR-7; assumption: A3]
- NFR-4 [Must] The system shall enforce audience and role boundaries in the release acceptance suite. [Measure: every negative case is denied and reveals no protected content when testing signed-out access, a non-member's direct members-only link, publication by an unapproved or different-group officer, evidence access by an ordinary user, and badge modification by a group officer.] [Source: UR-3, UR-4, UR-6, UR-10]
- NFR-5 [Must] The system shall meet the attendance-retention deadline for cancelled events. [Measure: no retrievable attendance record or linked name-visibility choice remains in service-managed stores by 30 elapsed days after cancellation, including when an appeal is open; test using an advanced clock and a restoration check.] [Source: UR-8; S5 supplies the 30-day limit]
- NFR-6 [Must] The system shall preserve RSVP privacy at initial use. [Measure: in every new-RSVP test, another attendee's view and response data contain neither that person's name nor account identifier before event-specific opt-in, including members-only events.] [Source: UR-2, UR-8]

## 5. User stories and acceptance criteria

### US-1 [Must] [Source: S1, UR-1, UR-9]

As a student, I want to follow groups and read their permitted events in my browser,
so that I do not need to check several channels.

Acceptance criteria:

- Given university sign-in succeeds, when I follow a group, its published university-wide content appears in my followed-group feed; after unfollowing, it no longer appears there.
- Given I am signed out, accessing the community feed requires university sign-in and returns no community content.
- Given the NFR-2 phone and screen-reader conditions, I can find an event and operate follow/unfollow with named controls and announced states.
- Given the populated NFR-1 pilot dataset, the sign-in, follow, and event-view checks retain the expected account and group associations.
- If FR-21 is included, two visible upcoming events appear in start-time order when I choose that sort.

### US-2 [Must] [Source: S1, S5, UR-2, UR-9]

As an attendee, I want to RSVP without disclosing my name by default,
so that I control who can see my attendance.

Acceptance criteria:

- Given an eligible event and no existing RSVP, submitting twice leaves one RSVP; another attendee sees no name or account identifier from it.
- Given I opt into showing my name for one event, eligible attendees can see it for that event only; opting out removes it again.
- Given I withdraw my RSVP, my own status changes to not attending and my name is absent from the attendee-facing list.
- The RSVP and visibility-choice steps pass the keyboard, screen-reader, and phone checks in NFR-2.

### US-3 [Must] [Source: S2, UR-3, UR-4, UR-5]

As a group officer, I want to share drafts and correct events for the right audience,
so that members receive reliable information.

Acceptance criteria:

- Given two approved officers in the same group, one can save a draft and the other can reopen, edit, and publish it; an unapproved or different-group account cannot publish it.
- Given a members-only event, a current member can view it, but a non-member using its direct link cannot; following the group does not change this result.
- Given a published event with an RSVP holder who remains eligible, saving a changed time or place creates their correction notice with the old and new values. An RSVP holder whose membership was revoked receives no members-only details.
- If FR-20 is included, a draft preview shows the attendee presentation without publishing a feed item.

### US-4 [Must] [Source: S3, UR-6]

As a moderator, I want to assess reports and hide content without losing evidence,
so that decisions can be reviewed during appeals.

Acceptance criteria:

- Given a report with a reason, I can see the reported content snapshot and reason; a report with an empty reason is rejected.
- Given I hide the reported event, ordinary users cannot retrieve it from feeds or a direct link, while its snapshot remains available in moderator-only evidence.
- A hide, restore, or appeal decision records the responsible moderator, content ID, action, timestamp, and reason; an ordinary user cannot retrieve that evidence.

### US-5 [Must] [Source: S2, S3, UR-3, UR-6]

As an officer of a moderated group, I want to appeal its moderation decision,
so that the group can contest a mistaken removal.

Acceptance criteria:

- Given a decision on my group's event, I can submit an appeal linked to it and later see the decision outcome.
- Given a decision for another group, I cannot submit its appeal or inspect its private appeal content; my own group's appeal view exposes neither reporter identity nor moderator-only evidence.

### US-6 [Must] [Source: S4, S6, UR-7, UR-10]

As a Student Affairs representative, I want badges to reflect completed group checks,
so that students can recognise checked identities during the pilot.

Acceptance criteria:

- Given a group with no verification record, its service badge is absent; recording an approved check as Student Affairs makes the official badge appear, and revocation removes it.
- Given a group officer tries to set the official verification field, the request is denied and the badge remains unchanged.
- With the NFR-1 dataset, the pilot's sequential sign-in, follow, publish, and RSVP checks complete without missing records or population-limit rejection.

### US-7 [Must] [Source: S5, UR-8, UR-2]

As the Data Protection Officer, I want attendance deleted after cancellation,
so that the service does not retain unnecessary personal associations.

Acceptance criteria:

- Given an approved officer cancels an event, new RSVPs are rejected and the event no longer appears in upcoming-event views.
- Given a cancelled event, its attendance is deleted by the NFR-5 deadline even if a moderation appeal is open; separate content evidence and the decision record remain subject to Q3.
- Given an attempt to save an extra personal-profile field such as a phone number, it is rejected under the A5 inventory.

### US-8 [Must] [Source: S6, UR-10]

As a student using the service, I want repeated identical announcements blocked,
so that a compromised account cannot flood my feed with the same post.

Acceptance criteria:

- Given a group successfully publishes an announcement, a second identical publication by either officer of that group within 60 seconds is rejected and creates no additional feed item.
- After the 60-second window the same content is not rejected by this particular duplicate rule; other publication permissions still apply.
- Given a suspicious visible event, I can submit its content and a reason for moderator review through FR-11, even if it bypassed the exact-repeat rule.

## 6. MoSCoW summary

- Must: UR-1, UR-2, UR-3, UR-4, UR-5, UR-6, UR-7, UR-8, UR-9, UR-10; FR-1, FR-2, FR-3, FR-4, FR-5, FR-6, FR-7, FR-8, FR-9, FR-10, FR-11, FR-12, FR-13, FR-14, FR-15, FR-16, FR-17, FR-18, FR-19; NFR-1, NFR-2, NFR-4, NFR-5, NFR-6; US-1, US-2, US-3, US-4, US-5, US-6, US-7, US-8.
- Should: FR-20 (officer preview), NFR-3 (provisional response-time target).
- Could: FR-21 (chronological sort).
- Won't this release: X-1 native mobile apps, X-2 direct messages, X-3 external users, X-4 payments, X-5 video hosting, X-6 AI recommendations.

Optional criteria explicitly labelled “if included” do not make FR-20 or FR-21
mandatory through a Must story. Mandatory phone and screen-reader support
remains part of the browser release.

## 7. Traceability

| Stakeholder need | User requirement | System requirement | User story |
|---|---|---|---|
| S1: one place for followed groups; release: university sign-in | UR-1 | FR-1, FR-2, FR-3 | US-1 |
| S1: less effort finding club events; A6 optional sort | UR-1 | FR-21 | US-1 |
| S1/S5: control public RSVP identity | UR-2 | FR-7, FR-8, NFR-6 | US-2 |
| S1: phone and screen-reader access | UR-9 | NFR-2 | US-1, US-2 |
| S2: shared drafts, approved publishers; A6 optional preview | UR-3 | FR-4, FR-5, FR-20 | US-3 |
| S2: members-only versus university audience | UR-4 | FR-3, FR-6, NFR-4 | US-3 |
| S2: inform people who RSVP'd about place/time changes | UR-5, UR-4 | FR-9 | US-3 |
| S3: reported content, reason, and retained evidence | UR-6 | FR-11, FR-12 | US-4 |
| S3: accountable decisions and group appeals | UR-6, UR-3 | FR-13, FR-14, NFR-4 | US-4, US-5 |
| S4: checked badges; S6: impersonation | UR-7, UR-10 | FR-15, FR-16, NFR-4 | US-6 |
| S4: 5,000 students and 200 groups | UR-7 | NFR-1 | US-1, US-6 |
| S1: usable feed; S4: pilot; A3 provisional workload | UR-1, UR-7 | NFR-3 | US-1 |
| S5: delete attendance after cancellation | UR-8 | FR-10, FR-19, NFR-5 | US-7 |
| S5: minimise personal data | UR-8 | FR-18 | US-7 |
| S6: repeated compromised-account announcements | UR-10 | FR-17 | US-8 |
| S6: suspicious phishing events can be reported | UR-10, UR-6 | FR-11 | US-8, US-4 |

## 8. Assumptions and open questions

### Assumptions

- A1: University-wide means authenticated university users, not the public internet. Group membership and officer approval are distinct permissions; following a group does not grant membership.

- A2: The 360-CSS-pixel viewport and VoiceOver/Safari combination are proposed minimum acceptance conditions, not stakeholder-supplied device specifications. Confirm the supported device and assistive-technology matrix with S1; passing this matrix does not establish universal accessibility.
- A3: NFR-3's 100 users, 5-second interval, 10-minute run, 2-second p95, and 1% error ceiling are provisional team targets. S4 supplied no peak traffic. Confirm or revise after measurement and peak-load clarification; no Orientation capacity promise is implied.
- A4: Exact-repeat blocking for the same group within 60 seconds is a proposed first abuse control. Identical means the same text and links after trimming leading/trailing whitespace. Modified phishing content is still possible and needs reports and moderation; no complete phishing-prevention claim is made.
- A5: Proposed minimum field inventory: university account identifier and display name; group membership and officer/verification roles; follows; event ID, RSVP account ID, and event-specific name-visibility choice; authored content; report content/reason/reporter ID; moderation actor/action/reason/time; appeal author/text/outcome. Do not collect phone numbers, addresses, location history, or behavioural advertising profiles. User-entered content may itself contain personal data. S5 must approve purposes and retention per field.
- A6: Officer preview (FR-20) and chronological sorting (FR-21) are optional team proposals supporting S2 and S1, respectively; the handout does not demand these features.
- A7: Correction notices are in-service notifications, not email or push guarantees. A former member does not receive members-only details after access is revoked. Ask S1/S2 to confirm this delivery channel and membership-change rule.
- A8: Private attendance is available only to the attendee for their own RSVP and to the service for corrections/deletion; no officer attendance-list access is assumed pending Q4. Moderator evidence access does not grant attendance access.

### Open questions

- Q1: Who supplies authoritative membership records and approves officers? Confirm with S2 and S4; university sign-in alone does not establish either permission.
- Q2: What is the actual Orientation launch date and expected peak concurrency? The 5,000 students are pilot population, not a stated simultaneous-user load.
- Q3: What evidence-retention period and redaction policy will S3/S5 approve? Attendance still has the 30-day cancellation deadline, regardless of appeal status.
- Q4: Do officers need attendance names or only counts, and may cancelled events retain opted-in public names? Proposed decision: remove all attendance associations by the deadline and grant no extra list access without S5 approval.
- Q5: What will the backup and restoration process do to honour attendance deletion? S5 must approve a design that cannot restore overdue attendance records to usable service data.
- Q6: What objective checks establish a verified group, who may review appeals, and how are compromised officer accounts suspended? Confirm with S4/S3 before implementation.
- Q7: How soon must correction notices appear, and how are notification failures retried or exposed? FR-9 specifies notice creation but no stakeholder-backed delivery-time guarantee.
