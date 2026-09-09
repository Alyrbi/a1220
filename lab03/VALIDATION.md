# CampusPulse requirements review

Name or team: Ali Yaarobi

Reviewer: Codex-assisted document review; no independent stakeholder approval claimed.

Date: 2026-09-09

## Validity

UR-1, UR-2, and UR-9 follow S1's actual needs: following clubs, choosing RSVP
name disclosure, and using phones/screen readers. UR-3–UR-5 follow S2's shared
drafts, approved publishing, audience restrictions, and event corrections.
UR-6 and FR-11–FR-14 follow S3's reports, evidence, decision records, and appeals.
UR-7/FR-15 use S4's verified-group check and pilot population. UR-8/FR-10 use
S5's data minimisation and 30-day cancellation deadline. UR-10/FR-16–FR-17 use
the impersonation and repeated-post scenarios from S6. These replace the local
earlier draft's unsupported leadership analytics and operational incident alerts.
Optional preview/sorting and operational targets are explicitly proposals A2–A6,
not statements attributed to the source notes.

## Consistency

FR-6 checks membership independently of following (A1), so UR-1 does not expose
members-only events. FR-8's voluntary name display remains within the event's
permitted audience; default privacy is checked by NFR-6. FR-9 does not disclose
members-only corrections to former members (A7). FR-12 preserves report evidence,
while revised FR-10 and NFR-5 require deletion of attendance despite an appeal;
these are separate data categories, resolving the S3/S5 tension without an
unapproved attendance-retention exception. Personal information embedded in
content still needs the redaction decision in Q3. Section 1 exclusions X-1–X-6
match the Won't list exactly. Optional FR-20/FR-21 criteria are conditional, so
Must stories do not silently upgrade those priorities.

## Completeness

The release boundary is represented: sign-in (FR-1), groups/badges (FR-15–FR-16),
following/feed (FR-2–FR-3), drafts/publication (FR-4–FR-5), audience (FR-6),
RSVP/privacy (FR-7–FR-8), corrections (FR-9), reporting/moderation/appeals
(FR-11–FR-14), cancellation/deletion (FR-19/FR-10), and repeat abuse (FR-17).
US-2 includes duplicate RSVP and privacy cases; US-3 includes non-member links
and unapproved publishers; US-4/US-5 include protected evidence and appeal
boundaries; US-6/US-8 include badge modification and repeated posts. Every
FR/NFR has an existing UR source and a traceability path to a story.

This is sufficient for the lab's requirements exercise, but implementation still
needs answers about membership/approval ownership (Q1), launch/traffic (Q2),
evidence redaction/retention (Q3), officer attendance access (Q4), backup deletion
(Q5), verification and incident procedures (Q6), and correction failure handling
(Q7). These are documented gaps rather than claims that all stakeholder policy
has already been resolved.

## Realism

The scope stays within the supplied browser pilot and excludes native apps,
payments, external users, video, direct messages, and AI recommendations.
NFR-1 uses S4's 5,000 students and 200 groups as a dataset-size check; it does
not infer 5,000 simultaneous users. NFR-3's load and latency values are proposed
in A3 and must be confirmed against Q2. NFR-2's device/test matrix and FR-17's
60-second exact-repeat rule are proposed in A2 and A4. Exact-repeat blocking
cannot stop every phishing variant, so reports and moderation remain necessary.
No team capacity or Orientation date was provided, so delivery before that date
cannot yet be guaranteed. The 30-day attendance deadline is source-backed,
while feasibility across backup/restoration requires Q5 to be resolved. There
has been no implementation performance test or stakeholder sign-off.

## Verifiability

FR-5 has an observable deny outcome for unapproved publishers; FR-6 can be
checked through member/non-member direct links; FR-8/NFR-6 have explicit
before-opt-in, after-opt-in, and opt-out observations. FR-11 rejects an empty
reason and retains a snapshot. FR-15/FR-16 use an active check record rather
than a vague claim that a group is trustworthy. FR-17 specifies the identity of
the group, duplicate definition (A4), and time window. Revised FR-10 gives a
recorded starting time, data to remove, deadline, and appeal boundary; NFR-5
adds an advanced-clock and restoration check. NFR-1–NFR-6 each state a measure
and condition, with unsupplied numeric targets labelled as assumptions.

UR-10 is intentionally customer-level protection language, not a promise to
prevent every attack; the pass/fail behaviours are FR-11, FR-16, and FR-17.
Q3/Q5/Q6/Q7 are still policy or operational design questions and must be answered
before claiming production readiness. The present checks validate the document,
not a running CampusPulse implementation.

## One requirement you revised

- Requirement ID: FR-10.
- Before: The system shall delete attendance data after an event is cancelled.
- What was wrong or missing: “After” had no deadline or clock origin, “attendance data” did not identify the affected records, and an appeal could be interpreted as allowing indefinite retention. It omitted S5's explicit 30-day limit.
- After: The system shall delete a cancelled event's RSVP records and linked name-visibility choices from service-managed stores within 30 elapsed days of the recorded cancellation time, without postponement for an appeal.
- Evidence or stakeholder to confirm the change: S5 supplies the cancellation deadline; S3 needs separate appeal evidence. Conflict 2 separates the two. Confirm backup/restoration treatment with S5 in Q5 and evidence redaction/retention with S3/S5 in Q3. The same wording is in REQUIREMENTS.md, its traceability row now names the deadline and separate appeal evidence, and US-7 checks the affected records.

## Final check

- [x] Stakeholder conflicts have a decision or a follow-up question.
- [x] Scope exclusions agree with the Won't list.
- [x] Every FR and NFR traces to a user requirement.
- [x] Every NFR contains a measurable target and condition.
- [x] Traceability rows use IDs that exist in the document.
- [x] The revised requirement has also been updated in the traceability table.
