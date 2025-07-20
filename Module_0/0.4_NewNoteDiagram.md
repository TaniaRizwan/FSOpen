```mermaid

sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user submits the form with text for a new note.

    browser->>server: POST https://fullstack-exampleapp.herokuapp.com/new_note
    activate server
    server->>browser: HTTP Status Code 302 
    Note right of browser: A new note is sent to the server. The server responds with a URL redirect message.
    deactivate server

    browser->>server: GET /notes
    activate server
    server->>browser: [{"content": "new_note", "date": "YYYY-MM-DD"}, ...]
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    Note right of browser: The browser re-renders the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    Note right of browser: The server creates a new note object and adds it to the array of notes
    deactivate server


