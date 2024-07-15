
# 0.4 New Note Diagram

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: SUBMIT FORM "text"=[string]

    Note right of Browser: Data to send: "note": [text]

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
  
    
    activate Server
    Note left of Server: Saves Data "note": [String] as new note
    Note left of Server: Proceeds to request Browser a redirection 
    Server-->>Browser: 302 Found REDIRECT to https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Server

    activate Browser       
    Note right of Browser: Executes Server request for a redirection    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Browser

    activate Server
    Server-->>Browser: Returns de notes page
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css

    activate Server
    Server-->>Browser: Returns main.css file with styles
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js

    activate Server
    Server-->>Browser: Returns main.js file with javascript coded to be executed
    deactivate Server

    activate Browser       
    Note right of Browser: Executes Javascript received by server and requests for data    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    deactivate Browser

    activate Server
    Server-->>Browser: Returns data.json: [{"content": "test", "date": "2024-07-15T07:53:17.198Z" }...]
    deactivate Server

    activate Browser       
    Note right of Browser: Translates JSON data to LI DOM elements and appends them to UL to render them.
    deactivate Browser

```
