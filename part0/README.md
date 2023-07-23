Part 0 Exercises:

0.4: New note diagram

sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: {note: "_PLACEHOLDER_NOTE_"}
    deactivate server

    The server redirects back to https://studies.cs.helsinki.fi/exampleapp/notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: {note: "_PLACEHOLDER_NOTE_"}
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes


0.5: Single page app diagram
Problem: Create a diagram depicting the situation where the user goes to the single-page app version of the notes app at https://studies.cs.helsinki.fi/exampleapp/spa.

sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: BASE HTML DOCUMENT
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ] // the json containing all notes
    deactivate server



0.6: New note in Single page app diagram
Problem: Create a diagram depicting the situation where the user creates a new note using the single-page version of the app.

sequenceDiagram
    participant browser
    participant server

    The User Enters the note in the Input Element and Presses the "Save" button

    browser: The Javascript reads the input element and adds to the "notes" variable.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa 
                      DATA:{
                              "content": "nice",
                              "date": "2023-07-23T15:45:50.631Z"
                            }
    activate server
    server-->>browser: {"message":"note created"}
    deactivate server

    
    browser: The Javascript redraws all the notes on the webpage.
