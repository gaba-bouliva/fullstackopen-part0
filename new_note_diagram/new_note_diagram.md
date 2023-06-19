# 0.4 New note diagram 
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_notes 

    Note right of browser: The post request contains a payload which has the note form data {note: 'value entered in input'}

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    Note right of browser: All notes are returned with the newly created note included in the HTML doc as links in a unordered list


    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    activate browser
    

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    deactivate browser
    activate server
    server-->>browser: [{"content": "Hello fullstack", "date": "2023-06-19T11:13:18.197Z"}, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```