```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: Input new note, click "submit"

    browser->>+server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: send form data with Content-Type:Json, {note: "newNote", date: "2024-09-22"} 
    Note right of server: Create new note {content: "newNote", date: "2024-09-22"}
    Note right of server: Add into notes
    server-->>-browser: 201 Created
    Note right of browser: Browser rerender the note list
