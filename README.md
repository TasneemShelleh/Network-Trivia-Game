# Network-Trivia-Game-main

A multiplayer network trivia game implemented using Python socket programming. The project uses UDP communication between a server and multiple clients, allowing players to join the game, receive trivia questions, submit answers, and view the leaderboard.

This project demonstrates basic networking concepts such as client-server communication, UDP sockets, threading, broadcasting messages, and handling multiple players.

## Project Overview

The goal of this project is to build a simple multiplayer trivia game over a network. The server manages the game, stores the questions, receives player answers, calculates scores, and broadcasts messages to all connected clients.

The client connects to the server, sends the username, listens for game messages, and allows the player to answer questions when they are received.

## Repository Structure

```text
Network-Trivia-Game-main/
│
├── server (3).py              # Main UDP trivia game server
├── client.py                  # UDP client used by players
├── NetworkProj_reprot.pdf     # Project report/documentation
└── README.md                  # Project documentation
```

## Features

* Multiplayer trivia game
* UDP socket communication
* Server-client architecture
* Multiple clients can join the same game
* Username registration
* Random question selection
* Timed question answering
* Score calculation
* Leaderboard display
* Option to continue with another round
* Threading for handling clients and listening for messages

## Technologies Used

* Python
* Socket Programming
* UDP Protocol
* Threading
* Random question selection
* Client-server networking

## How the Game Works

```text
Start Server
    ↓
Clients Connect to Server
    ↓
Players Enter Usernames
    ↓
Server Waits for Minimum Number of Players
    ↓
Server Starts the Trivia Round
    ↓
Questions Are Sent to All Players
    ↓
Players Submit Answers
    ↓
Server Checks Answers
    ↓
Scores Are Updated
    ↓
Leaderboard Is Displayed
    ↓
Players Can Continue or End the Game
```

## Server Description

The server file is:

```text
server (3).py
```

The server is responsible for:

* Creating a UDP socket
* Binding to host `0.0.0.0`
* Listening on port `5689`
* Receiving usernames from clients
* Storing connected clients
* Broadcasting messages to all players
* Selecting random trivia questions
* Receiving answers from clients
* Checking answers
* Updating scores
* Displaying the leaderboard

## Client Description

The client file is:

```text
client.py
```

The client is responsible for:

* Creating a UDP socket
* Connecting to the server
* Sending the username to the server
* Listening for messages from the server
* Detecting when a question is received
* Allowing the user to enter an answer
* Sending the answer back to the server

## Game Settings

The server uses the following settings:

```python
HOST = "0.0.0.0"
PORT = 5689
BUFFER_SIZE = 1024
MIN_PLAYERS = 2
WAIT_FOR_PLAYERS = 20
QUESTION_DELAY = 10
ANSWER_TIMEOUT = 10
```

| Setting            | Description                                        |
| ------------------ | -------------------------------------------------- |
| `HOST`             | Server listens on all available network interfaces |
| `PORT`             | Port number used by the game                       |
| `BUFFER_SIZE`      | Maximum size of received messages                  |
| `MIN_PLAYERS`      | Minimum number of players required to start        |
| `WAIT_FOR_PLAYERS` | Waiting time before starting the game              |
| `QUESTION_DELAY`   | Delay before sending each question                 |
| `ANSWER_TIMEOUT`   | Time allowed for players to answer                 |

## Question Database

The server contains a small built-in question database.

Example questions:

```text
What is the capital of France?
Who wrote 'Hamlet'?
What is 5 + 7?
What is the boiling point of water (Celsius)?
Which planet is known as the Red Planet?
```

Each question has one correct answer stored in the server.

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Network-Trivia-Game-main.git
```

### 2. Open the Project Folder

```bash
cd Network-Trivia-Game-main
```

### 3. Run the Server

Open a terminal and run:

```bash
python "server (3).py"
```

The server will start on:

```text
0.0.0.0:5689
```

You should see output similar to:

```text
Server started at 0.0.0.0:5689
```

### 4. Run the Clients

Open another terminal for each player and run:

```bash
python client.py
```

Each client will be asked to enter a username:

```text
Enter your username:
```

At least two players are required to start the game.

## Running on the Same Computer

If the server and clients are running on the same computer, keep this line in `client.py`:

```python
SERVER_IP = "127.0.0.1"
```

Then run the server in one terminal and run multiple clients in separate terminals.

## Running on Different Computers

If the clients are running on different devices in the same network, update `SERVER_IP` in `client.py` to the server computer’s local IP address.

Example:

```python
SERVER_IP = "192.168.1.10"
```

Make sure all devices are connected to the same network and that the firewall allows Python/network access.

## Example Game Flow

```text
Server started at 0.0.0.0:5689

Client 1:
Enter your username: Tasneem

Client 2:
Enter your username: Layan

Server:
Tasneem has joined the game!
Layan has joined the game!
Game will start in 20 seconds. Get ready!

Question 1: What is the capital of France?
Enter your answer: Paris

Time's up! The correct answer was: Paris
Tasneem answered correctly!

End of the round! Current leaderboard:
Tasneem (1+0+1) = 2 points
Layan (0+1+1) = 2 points
```

## Important Notes

* The server must be running before starting the clients.
* At least two clients are needed to start the game.
* The project uses UDP, so messages are not guaranteed to arrive like TCP.
* If running on different computers, update the server IP in `client.py`.
* If the game does not connect, check the firewall and network settings.
* The server file name can be renamed from `server (3).py` to `server.py` for a cleaner GitHub structure.

## Possible Improvements

* Add more trivia questions
* Store questions in an external file
* Add categories and difficulty levels
* Add a graphical user interface
* Improve score tracking across multiple rounds
* Add player disconnection handling
* Use TCP if reliable delivery is required
* Add better validation for repeated answers
* Add a maximum number of players

## Learning Outcomes

This project demonstrates:

* How to create UDP sockets in Python
* How client-server communication works
* How to send and receive messages over a network
* How to handle multiple clients
* How to use threads in networking applications
* How to broadcast messages to connected clients
* How to build a simple multiplayer game

## Author

Tasneem Shelleh

