# Real-Time Chat Room System

A real-time chat room system implemented in Python 3 using the `websockets` library and `asyncio` for non-blocking asynchronous communication. This project demonstrates a Client-Server architecture and a Publisher-Subscriber (Pub-Sub) model.

## Features

- **Concurrent Client Handling**: The server concurrently handles multiple client connections asynchronously.
- **Unique Usernames**: Users must log in with a unique username; duplicate usernames are rejected by the server.
- **Chat Rooms (Pub-Sub Model)**: Users can join specific chat rooms (e.g., "sports", "technology"). The server acts as a broker to broadcast messages to all subscribers in that room.
- **Message History**: Chat history is persisted in text files (e.g., `sports.txt`). Late joining clients automatically receive the last 5 messages from the room's history.
- **Non-blocking Input**: The client utilizes background tasks to display incoming messages smoothly without interrupting the user's typing prompt.

## Prerequisites

- Python 3.7 or higher
- `websockets` library

### Installing Dependencies

You can install the required `websockets` library using `pip`:

```bash
pip install websockets
```

## How to Run

### 1. Start the Chat Server
The server must be started first. It listens for incoming WebSocket connections on `ws://localhost:2024`.

Open a terminal and run:
```bash
python chat_server.py
```
*Expected Output:*
```text
[SERVER] Starting Chat Manager on ws://localhost:2024...
```

### 2. Start Chat Clients
Open one or more separate terminals to act as connected users.

```bash
python chat_client.py
```

### 3. Usage Flow
- **Login**: Upon running the client, you will be prompted for a username.
- **Join Room**: Enter the name of the room you wish to join (e.g., `lobby`, `gaming`). If the room doesn't exist, it will be created on the fly.
- **Chatting**: Start typing your messages and press `Enter`. Other users in the same room will see your messages in real-time.
- **Exit**: Type `exit` or `quit` to leave the chat room.

## Project Structure

- `chat_server.py`: Contains the server-side logic, connection handling, chat room management, data structures for connected users, and message logging.
- `chat_client.py`: Contains the client-side logic handling WebSocket connections, background message listening, and a non-blocking user input loop.
- `[room_name].txt`: Auto-generated log files that store the message history for each respective room.
