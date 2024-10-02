```mermaid

sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Request the URL: https://studies.cs.helsinki.fi/exampleapp/spa
    activate Browser
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    deactivate Browser
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    activate Browser
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    deactivate Browser
    activate Server
    Server-->>Browser: CSS file (main.css)
    activate Server

    activate Browser
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    deactivate Browser
    activate Server
    Server-->>Browser: JavaScript file (spa.js)
    deactivate Server
    Note right of Browser: The Browser starts executing the JavaScript code that fetches the JSON<br>from the Server and gives event handler to the form

    activate Browser
    Browser-->>User: Show Website with styles
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate Server
    deactivate Browser
    Note right of Browser: The Browser executes the callback function that renders the notes

    Browser-->>User: Show the rendered notes.

    
