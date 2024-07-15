
# 0.6: New note in Single page app diagram

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: SUBMIT FORM "text"=[string]

    activate Browser
    Note right of Browser: Converts data from FORM to JSON: {"Content": [text], "date": [NOW]}
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa {"Content": [STRING], "date": [DATE]}
    deactivate Browser

    activate Server
    Note left of Server: Adds new note to notes
    Server-->>Browser: 201 Created {"message": "note created"}
    deactivate Server

    activate Browser
    Note right of Browser: Renders new LI element appended to UL showing the new note
    deactivate Browser
```
