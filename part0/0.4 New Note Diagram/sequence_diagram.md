```mermaid

sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Fill the form with a new note and clicks on "Save".
    activate Browser
    
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Browser
    Note right of Browser: Form Data [note: Test from form]
    activate Server
    Server-->>Browser: HTTP status code 302 (Redirect)
    activate Browser
    Note over Server: The server saves the note on the array of notes.
    deactivate Server
    
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Browser
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    activate Browser
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    deactivate Browser
    activate Server
    Server-->>Browser: CSS file
    activate Server

    activate Browser
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    deactivate Browser
    activate Server
    Server-->>Browser: JavaScript file
    deactivate Server
    Note right of Browser: The Browser starts executing the JavaScript code that fetches the JSON from the Server

    activate Browser
    Browser-->>User: Show Website with styles
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "Test from form", "date": "2024-10-02" }, ... ]
    deactivate Server
    deactivate Browser
    Note right of Browser: The Browser executes the callback function that renders the notes

    Browser-->>User: Show the rendered notes with the new one.
