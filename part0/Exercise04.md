```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: Input new note, click "submit"

    browser->>+server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note right of browser: Send Form data
    Note right of server: Create new note {content: "newNote", date: new Date()}
    Note right of server: Add into notes
    server-->>-browser: Redirect to https://studies.cs.helsinki.fi/exampleapp/notes

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    server-->>-browser: HTML document

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    server-->>-browser: the css file

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    server-->>-browser: the javascript file
    Note right of browser: Browser starts executing the javascript code that fetches the Json from server

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server-->>-browser: [{"content": "newNote", "date": "2024-09-22"}, ...]

    Note right of browser: Browser executes the callback funtion that renders the notes