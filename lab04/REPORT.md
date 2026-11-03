# Lab 04 report

Student name: Ali Humaid Sulaiman Yaarobi

Date: 3 November 2026

Repository: https://github.com/Alyrbi/a1220

Status: Code and required browser/API checks completed with AI assistance. These are observed checks performed by Codex, not a claim that the student independently performed or reviewed them. Student review and explanation remain part of learning the lab.

## Exercise 1 - Explore and make a commit

- Working folder: `/Users/ali.yaarobi/a1220/lab04` (the existing checkout is named `a1220`, rather than the sheet's illustrative `ai1220`).
- Git repository root: `/Users/ali.yaarobi/a1220`.
- Initial report commit hash (`Start lab04 report`): `72382d5d1e8d680f5349c94e8fa014339afedf45`.
- Files included in that commit: only `lab04/REPORT.md`, verified using `git show --stat`.
- What was saved in that commit: the supplied report template with the student's name entered; code changes were not included.
- `backend.py` owns the playlist: its `songs` list and `next_id` variable live in the server process. It validates additions and supplies the authoritative stored records.
- `index.html` displays the playlist: the browser builds list items from the server's JSON and handles form interaction.
- Initial loading: the server serves the page at `/`; its script calls `loadSongs()`, which requests `GET /songs`. `requestJSON` parses the returned list, and `loadSongs` renders `First Light / Demo Band`.
- Access/setup observations: no account or usage-limit blocker required instructor support. The supplied README identifies this as a recreated starter; that provenance is retained. The initial inspection ran using the system Python 3.9.6; after noticing the sheet requires 3.10+, the full final browser/API checks ran using bundled Python 3.12.14. Safari's inspector did not display correctly, so the required Network inspection used Chrome Guest mode.

## Exercise 2 - Backend

- `create_song(payload)` reads `title` and `artist`, checks each is a string, trims it, and checks the trimmed length is 1–80 inclusive. It collects both validated values before changing global state.
- Only the assigned ID and validated title/artist are stored. Extra fields are ignored and duplicate titles are allowed.
- Invalid input raises a helpful `ValueError`. The supplied handler converts this into HTTP 400 JSON. Since validation happens before `songs.append` or incrementing `next_id`, a rejected request changes neither.
- Before editing the frontend, a direct request with title `  Backend Check  ` and artist `Demo Artist` returned 201 and `{"id": 2, "title": "Backend Check", "artist": "Demo Artist"}`.
- A direct request with a spaces-only title returned 400 and `{"error": "title must contain 1 to 80 characters after trimming."}`. The stored list still had two entries. These initial direct checks used system Python; the final checks below used Python 3.12.14 after a clean restart.

## Exercise 3 - Frontend

- Visible heading: `My playlist`.
- `sendSong(title, artist)` returns `requestJSON("/songs", options)` with method `POST`, header `Content-Type: application/json`, and body `JSON.stringify({ title, artist })`. This sends the supplied form values; the backend remains responsible for trimming and validation.
- The helper returns parsed JSON for successful requests and throws the server's error message for a failure. Returning its promise allows the existing form handler to await the real result.
- Accepted form submission: `Blue Sky / Test Duo` appeared once and both fields cleared; refreshing kept it because the server process retained the list.
- Rejected form submission: three spaces plus `Sample Artist` displayed the server error, kept both input values and left all six then-current list entries unchanged. Correcting the title to `Morning Steps` and submitting with Enter succeeded.
- The displayed list was compared with `GET /songs`, including direct additions, and the Network panel confirmed that a successful POST is followed by a GET of the authoritative list.

## Exercise 4 - Actual verification observations

| Check from page 3 | Actual observation | Pass/fail |
| --- | --- | --- |
| Fresh start: page and GET show only First Light / Demo Band, ID 1 | Both the page and HTTP 200 JSON contained the single seed record. | PASS |
| Form: Blue Sky / Test Duo appears once; fields clear | Added as ID 2, one visible entry, both inputs empty. | PASS |
| Refresh: both songs remain | Seed and Blue Sky remained after reload. | PASS |
| Form: another invented song with different values works | Evening Path / Paper Quartet appeared as ID 3. | PASS |
| Direct addition: 201, trimmed values, next unused ID; visible after refresh | Quiet Road / Sample Artist returned ID 4; surrounding spaces and an extra field were not stored; refresh showed it. | PASS |
| Whitespace-only title: 400; no new song | Server returned the length error and the full list remained equal to its earlier value. | PASS |
| Missing artist: 400 | `artist must be provided as a string.`; no state change. | PASS |
| Numeric title: 400 | `title must be provided as a string.`; no state change. | PASS |
| 81-character title: 400 | Rejected with the 1–80 length error. | PASS |
| 80-character title: accepted | 80-character title and artist accepted together as ID 5. | PASS |
| Rejected additions do not consume an ID | Ten invalid field cases between successful IDs 4 and 5 all left the list unchanged; next accepted ID was 5. | PASS |
| Form rejection: visible error, retained inputs, unchanged list | Spaces-only title and Sample Artist remained; error visible; six entries before and after. | PASS |
| Corrected form submission succeeds | Morning Steps / Sample Artist added as ID 7; form cleared. | PASS |
| Keyboard: Tab and Enter work | Tab from Title focused Artist; Enter in Artist submitted the corrected song. | PASS |
| Network: POST payload, 201 status, JSON response, following GET | Chrome Network showed POST /songs for Network Song / Demo Signals, 201 JSON with ID 8, then GET /songs with 200 and the stored list. | PASS |
| Restart and refresh: only the seed song remains | After terminating and restarting Python 3.12.14, page and GET returned only ID 1. | PASS |

Additional boundary checks used both fields: missing, numeric, boolean, blank and 81-character values all returned 400; 80-character values succeeded. A second `Quiet Road / Sample Artist` was accepted as ID 6, confirming duplicates are allowed. These checks were run against the real HTTP server, not inferred from code.

### One successful request and response

Request method and path: `POST /songs` (observed in Chrome Network).

Request headers: `Content-Type: application/json`.

Actual request body:

```json
{"title":"Network Song","artist":"Demo Signals"}
```

Actual response status and headers: `201 Created`; `Content-Type: application/json`; `Cache-Control: no-store`; `Content-Length: 60`.

Actual response body:

```json
{"id": 8, "title": "Network Song", "artist": "Demo Signals"}
```

The following `GET /songs` returned 200 with eight stored records, and the page displayed `Network Song / Demo Signals` once.

### One failed request and response

Request method and path: `POST /songs` (direct HTTP boundary check).

Request headers: `Content-Type: application/json`.

Actual request body:

```json
{"title":"   ","artist":"Valid Artist"}
```

Actual response status and headers: `400 Bad Request`; `Content-Type: application/json`.

Actual response body:

```json
{"error": "title must contain 1 to 80 characters after trimming."}
```

The complete list was compared before and after every rejected request and remained identical. The last accepted ID before this group was 4; the next accepted record had ID 5, so rejected requests did not consume IDs.

### One code change reviewed during assisted completion

File and change: `backend.py`, completing `create_song` with a validation loop before mutation.

Explanation: both fields must be valid before the song is appended. A valid title paired with an invalid artist therefore cannot leave a partial record or advance the ID. The request's extra fields are excluded when the stored dictionary is constructed.

Observed result: missing/invalid artists and titles each produced HTTP 400 with no list change; the next valid record used the next consecutive ID. This matches the contract. An AST comparison confirmed the supplied HTTP setup outside `create_song` was unchanged.

## Submission

- Final code/report commit: `761436e9bfcfec79d4acd97451e9ed99e40aee29` (`Complete lab04 playlist`), recorded in this subsequent evidence commit.
- Files reviewed: `backend.py`, `index.html`, `REPORT.md`, `README.md`, `.gitignore`, plus the supplied lab sheet. Only the marked Python function, the marked JavaScript function and visible heading were changed in application code. The README's completion checklist was updated to reflect the checks above.
- Push and GitHub verification: pushed to `origin/main` on 3 November 2026. Remote `refs/heads/main` was verified as `60978de9d1543675572eeff4d0d39e77a47a34c2`, containing this lab and its completion commit. All six lab04 files were confirmed in that tracked tree.
- Optional stretch: not attempted; required functionality is complete.
