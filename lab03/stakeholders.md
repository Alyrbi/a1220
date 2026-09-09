# CampusPulse stakeholder analysis

Name or team: Ali Yaarobi

Date: 2026-09-09

Evidence: S1–S6 in the Lab 3 student sheet, page 2. Power and interest are
planning judgments based on those roles, not additional stakeholder statements.

## S1

- Stakeholder: Student attendee, including phone and screen-reader users.
- Stakeholder type: end user.
- Power-interest quadrant: keep informed (high interest, limited formal authority).
- Main goal: Follow clubs and find their events and announcements in one place.
- Main concern: An RSVP must not reveal the student's name publicly without their choice; the browser service must work on phones and with screen readers.
- How you would involve or monitor this stakeholder: Review follow and RSVP prototypes with students, including screen-reader users; ask them to check the default privacy setting and report navigation problems.

## S2

- Stakeholder: Group officer.
- Stakeholder type: end user.
- Power-interest quadrant: key player (high interest and control over group content).
- Main goal: Share drafting work with other officers, publish to the correct audience, and inform attendees about event changes.
- Main concern: Unapproved accounts publishing, members-only information leaking, or people missing a changed place or time.
- How you would involve or monitor this stakeholder: Walk through a two-officer draft, membership boundaries, and a venue correction; confirm who approves officers and who may see private attendance records.

## S3

- Stakeholder: Campus moderator.
- Stakeholder type: operations.
- Power-interest quadrant: key player (high interest and authority to hide content).
- Main goal: Act on a report with its content and reason, while preserving evidence for an appeal.
- Main concern: Hiding an event could destroy evidence, or a decision could have no accountable decision-maker.
- How you would involve or monitor this stakeholder: Review report, hide, and appeal scenarios; confirm evidence access and retention with S5 before implementation.

## S4

- Stakeholder: Student Affairs.
- Stakeholder type: business.
- Power-interest quadrant: key player (sponsor with approval and deadline authority).
- Main goal: Launch a pilot for 5,000 students and 200 groups before Orientation Week; an official badge must indicate a completed group check.
- Main concern: An unverified group appearing official, or a release that cannot support the pilot or misses the deadline.
- How you would involve or monitor this stakeholder: Confirm verification and launch acceptance rules, demonstrate the badge workflow, and ask for the actual Orientation date and expected peak traffic.

## S5

- Stakeholder: Data Protection Officer.
- Stakeholder type: regulator.
- Power-interest quadrant: keep satisfied (high policy authority; involve closely in privacy decisions rather than routine feature design).
- Main goal: Minimise personal data, make RSVP lists private initially, and delete cancelled-event attendance data within 30 days.
- Main concern: Unnecessary collection, public attendance disclosure, or moderation retention being used to keep attendance indefinitely.
- How you would involve or monitor this stakeholder: Review a field inventory, attendance access tests, cancellation deletion evidence, and the separation of moderation evidence from attendance data.

## S6

- Stakeholder: Impersonators and people controlling compromised group accounts, as described by the abuse cases.
- Stakeholder type: negative stakeholder.
- Power-interest quadrant: keep informed (monitor for threats: high interest in exploiting the service; low legitimate authority). Here monitoring means observing abuse signals, not sharing defensive information with attackers.
- Main goal: The attacker's goal is to impersonate a verified group and publish phishing content, or repeatedly post an announcement from a compromised account.
- Main concern: From the product's viewpoint, false trust in badges and repeated posts could harm students. S6 supplies threat scenarios, not a cooperative interviewee's preferences.
- How you would involve or monitor this stakeholder: Exercise spoofed-badge and repeated-publication scenarios; monitor rejected duplicate posts and reports without collecting unnecessary personal data.

## Conflicts to resolve

### Conflict 1

- Stakeholders: S2 and S1/S5.
- What conflicts: Officers need to reach people who RSVP'd, but students require private attendance by default and control over public names.
- Proposed decision or follow-up question: Send corrections through the service to eligible RSVP holders without exposing a public recipient list. Keep attendance private unless each attendee opts into showing their own name. Ask S2 and S5 whether officers need any attendance-list access beyond a count; do not assume they do.

### Conflict 2

- Stakeholders: S3 and S5.
- What conflicts: Moderators need evidence after hiding an event, while cancelled-event attendance data must be deleted within 30 days.
- Proposed decision or follow-up question: Preserve the reported content, reason, and decision record separately from attendance. An appeal does not extend the attendance deadline. Ask S3 and S5 to approve a separate evidence-retention period and redaction rules for personal data embedded in reported content.

### Conflict 3

- Stakeholders: S4 and S1.
- What conflicts: A deadline before Orientation and a large pilot can pressure the team to drop phone or screen-reader support.
- Proposed decision or follow-up question: Keep the essential follow/RSVP tasks accessible and defer optional sorting and preview conveniences. Ask S4 for the actual launch date and peak-traffic estimate before committing to a delivery schedule or load target.
