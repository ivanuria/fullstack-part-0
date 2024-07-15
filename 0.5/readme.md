
# 0.5: Single page app diagram

```mermaid
sequenceDiagram
    participant Browser
    participant Server

    activate Browser       
    Note right of Browser: Executes Server request for a redirection    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    deactivate Browser

    activate Server
    Server-->>Browser: Returns de notes page
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css

    activate Server
    Server-->>Browser: Returns main.css file with styles
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js

    activate Server
    Server-->>Browser: Returns spa.js file with javascript coded to be executed
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
