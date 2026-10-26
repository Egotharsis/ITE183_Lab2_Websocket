# ITE183_Lab2_Websocket

ITE183 – Web Systems and Technologies | Laboratory 2: WebSocket Server

An event-driven HTTP and WebSocket chat server built with the Bonezegei Scripting Language (v1.3.3). The server serves a static multi-client chat page, returns a custom 404 page for undefined routes, and broadcasts every received message to all connected clients in real time.

## Project Structure

```text
.
├── .gitattributes      # *.bzg highlighted as JavaScript on GitHub
├── LICENSE             # MIT License
├── README.md
├── app.bzg             # HTTP + WebSocket server (port 8000)
├── package.json        # Bonezegei package manifest (depends on http)
└── public/
    ├── index.html      # Multi-client WebSocket chat client
    └── 404.html        # Custom 404 page
```

## Requirements

- Bonezegei v1.3.3 (`bonezegei -v`)

## Usage

```bash
# install all dependencies
bzg install

# run the app
bzg run
```

Open `http://localhost:8000` in two or more browser windows and send a message from any of them; it appears in every window. Any other path (e.g. `http://localhost:8000/abc`) returns the custom 404 page.

## Server Events

| Event | Behavior |
|---|---|
| `server.get` | Serves `public/index.html` for `/`, otherwise `public/404.html` |
| `server.onConnect` | Logs the new client ID and sends it a welcome message |
| `server.onData` | Logs the message and broadcasts it to all clients via `server.sendAll()` |
| `server.onDisconnect` | Logs the disconnected client ID |

## Author

Jerrald Stephen M. Cañoneo — BSIT, MSU-IIT
