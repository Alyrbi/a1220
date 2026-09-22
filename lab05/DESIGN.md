# Campus Workshop Board - Design notes

Name: Ali Alyaarbi

Student ID: 25011226

## Diagram files

Each export is one view. The DOT files are editable diagram sources; they do not implement the application.

| View | Editable source | Export |
|---|---|---|
| 01-context | [01-context.dot](diagrams/source/01-context.dot) | [SVG](diagrams/exports/01-context.svg) · [PDF](diagrams/exports/01-context.pdf) |
| 02-containers | [02-containers.dot](diagrams/source/02-containers.dot) | [SVG](diagrams/exports/02-containers.svg) · [PDF](diagrams/exports/02-containers.pdf) |
| 03-components | [03-components.dot](diagrams/source/03-components.dot) | [SVG](diagrams/exports/03-components.svg) · [PDF](diagrams/exports/03-components.pdf) |
| 04-code | [04-code.dot](diagrams/source/04-code.dot) | [SVG](diagrams/exports/04-code.svg) · [PDF](diagrams/exports/04-code.pdf) |
| 05-dynamic | [05-dynamic.dot](diagrams/source/05-dynamic.dot) | [SVG](diagrams/exports/05-dynamic.svg) · [PDF](diagrams/exports/05-dynamic.pdf) |

## One structural choice (Exercise 2)

I chose one Python backend with PostgreSQL because a small team can maintain it easily for 200 students, while database transactions keep reservations safe when requests overlap.

## Your components (Exercise 3)

All six components belong to the Board API application; their interfaces and exchanged data are shown in `03-components`.

| Name | Job | Customer rule(s) served |
|---|---|---|
| Board Endpoints | Receive browser requests, require verified identity, route operations, and return only authorised results. | R1–R6 |
| Identity Gateway | Ask Campus Identity to verify the supplied credential and return a trusted student ID, name, and email, or reject it. | R1, R4 |
| Workshop Service | Validate new workshops, assign the creator as owner, enforce owner-only publishing/attendee access, and return published summaries with the caller's own reservation. | R2, R3, R5 |
| Reservation Rules | Return an existing reservation or atomically reserve one seat; request email only after committing a new reservation. | R4, R5, R6 |
| Board Repository | Store and query workshops/reservations; provide a transaction that locks the workshop before checking or inserting a reservation. | R2–R5 |
| Mail Gateway | Request one confirmation from University Mail and report `Sent` or `Unavailable`. | R6 |

## Reservation operation (Exercise 4)

`reserve(identity: IdentityResult, workshop_id: WorkshopId) -> ReservationResult`

- `IdentityResult = VerifiedStudent(student_id: StudentId, name: str, email: Email) | Unverified`. Only Identity Gateway creates a verified identity; IDs and email supplied in a browser request are not trusted as identity.
- `ReservationResult = Created(reservation: Reservation, email: Sent | Unavailable) | Existing(reservation: Reservation) | Rejected(reason: Unverified | NotFound | NotPublished | Full)`.
- IDs are opaque UUID-backed types. `Reservation` contains its ID, workshop ID, student ID, verified name/email snapshot, and creation time. Existing reservations are returned without modifying this record.

The invariant is **at most one reservation per student per workshop, and no more reservations than the workshop's capacity**. An unverified request returns immediately without accessing or changing reservations. For a verified request, Board Repository starts a PostgreSQL `READ COMMITTED` transaction and locks the workshop row using `SELECT ... FOR UPDATE`. Once that lock is acquired, it reads the existing reservation in a new statement. If one exists, it returns it unchanged, even when the workshop is full, and sends no email. Otherwise it checks publication and counts seats, rejects a full workshop, or inserts one reservation and commits.

All reservation inserts go through that same workshop lock, held until commit or rollback. A competing request waits, then reads the committed reservations using fresh statements, so two requests cannot both claim the last seat. A database `UNIQUE(workshop_id, student_id)` constraint also prevents duplicates. Capacity is fixed at creation in this design; editing, cancellation, and unpublishing are outside the brief. Only after a new reservation commits does Mail Gateway make one send request; a mail failure leaves the reservation intact and triggers no automatic retry.

## Ari's incident (Exercise 5)

| Observation | Result |
|---|---|
| Stored state before | W17, “Build a tiny game”, owner S10, published, capacity 3. S21 and S22 have reservations; S23 has none. Two seats occupied, one remaining. |
| Stored state after | W17 and its owner are unchanged. S21 and S22 keep their reservations. A new reservation R23 for W17/S23 stores Ari's verified name and `ari@example.invalid`. Three seats occupied, zero remaining. R23 is a readable diagram alias for a generated reservation ID. |
| Message Ari sees | “Your place in Build a tiny game is reserved. Confirmation email is unavailable.” Refreshing still shows Ari's reservation and zero remaining seats. |

## References used to check the design

- [C4 diagrams and levels](https://c4model.com/diagrams)
- [C4 dynamic diagrams](https://c4model.com/diagrams/dynamic)
- [PostgreSQL row locking](https://www.postgresql.org/docs/current/explicit-locking.html#LOCKING-ROWS)
