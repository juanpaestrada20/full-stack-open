```mermaid

sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Fill the form with a new note and clicks on "Save".
    activate Browser
    
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    deactivate Browser
    Note right of Browser: Form Data: {"content":"New Note","date":"2024-10-02T23:19:26.186Z"}
    activate Server
    Server-->>Browser: HTTP status code 201 (Created)
    Note over Server: The server saves the note on the array of notes.
    deactivate Server
    
    activate Browser
    Note right of Browser: The Browser executes the function to reDraw the notes
    Browser-->>User: Show the rendered notes with the new one.
    deactivate Browser
