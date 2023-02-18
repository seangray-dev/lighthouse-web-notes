## client.js

- This file uses the net module to create a TCP connection with the game server.
- `connect` function creates a connection with the specified IP address and port number.
- The `setEncoding` function specifies that incoming data should be interpreted as text.
- The `on` function registers an event listener for incoming data.
- The `connect` function registers an event listener for connection event and sends an initial message with the name of the client.

## constants.js

- This file exports two objects with hard-coded values:
  - `IP` and `PORT` are the IP address and port number for the game server.
  - `movementCommands` and `specialMessage` are objects that map keys to specific messages that will be sent to the server.

## input.js

- This file exports a function that handles user input and sends it to the server.
- `setupInput`function takes in a connection object and sets up the stdin input interface.
- The `stdin` object sets raw mode to listen for keystrokes, sets the encoding of the input to UTF-8 and resumes the stdin stream.
- The `handleUserInput` function is called whenever there is input from the user.
- The function checks if the input is a specific key (i.e., "w", "a", "s", "d", "m", "n", "y", "e") and sends the corresponding message to the server via the connection object.
- The `areDirectionsOpposite` function is a helper function that checks if two directions are opposite.
- The function is used to make sure the snake can't turn back on itself.

## play.js

- This file imports the `connect` function from `client.js` and `setupInput` function from `input.js`.
- The `connect` function returns a connection object that is stored in the `conn` variable.
- The `setupInput` function is called and passed the connection object `conn`.
- This sets up the input interface so the user can control the snake.
