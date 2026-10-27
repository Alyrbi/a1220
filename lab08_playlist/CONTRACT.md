# Playlist API contract

All paths are relative to http://127.0.0.1:8000. Fields use snake_case. Error responses use an `error` field containing a message for the user.

## 1. Get all songs

Method: GET  
Path: /songs  
Request body: none  
Response status: 200  
Response body (the three starting songs):

```json
[
  {"id": 1, "title": "Blue Monday", "artist": "New Order", "votes": 3},
  {"id": 2, "title": "Clocks", "artist": "Coldplay", "votes": 1},
  {"id": 3, "title": "Dancing Queen", "artist": "ABBA", "votes": 0}
]
```

## 2. Add a song

Method: POST  
Path: /songs  
Request body (example):

```json
{"title": "Yellow", "artist": "Coldplay"}
```

Response status: 201  
Response body (example on a fresh server):

```json
{"id": 4, "title": "Yellow", "artist": "Coldplay", "votes": 0}
```

The server trims surrounding whitespace; missing, non-string, empty, or whitespace-only fields are refused.

Error status (title or artist missing or empty): 400  
Error body:

```json
{"error": "Title and artist are required."}
```

## 3. Vote for a song

Method: POST  
Path: /songs/{id}/votes  
Request body: none  
Response status: 200  
Response body (example for id 1 on a fresh server):

```json
{"id": 1, "title": "Blue Monday", "artist": "New Order", "votes": 4}
```

Error status (no song with that id): 404  
Error body (example for id 99999):

```json
{"error": "There is no song 99999."}
```
