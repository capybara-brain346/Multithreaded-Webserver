# MultiThreaded Client-Server Application

This repository contains a simple multithreaded client-server application in Java, where a `Server` accepts connections from multiple `Client` instances concurrently. The server sends a greeting message to each client upon connection.

## Table of Contents

1. [Features](#features)
2. [Requirements](#requirements)
3. [Code Structure](#code-structure)
4. [Setup and Running the Application](#setup-and-running-the-application)
5. [How It Works](#how-it-works)
6. [Troubleshooting](#troubleshooting)
7. [Contributing](#contributing)
8. [License](#license)

---

## Features

- **Multithreaded Server**: The server can handle multiple client connections simultaneously by spawning a new thread for each client.
- **Client Requests**: Each client sends a greeting message to the server and receives a response.
- **Socket Communication**: Demonstrates basic socket programming in Java with try-with-resources for resource management.

## Requirements

- **Java JDK 8+**
- **IDE**: Any Java IDE (e.g., IntelliJ IDEA, Eclipse) or command-line tools.
- **Network Configuration**: Make sure no firewall or network restrictions block the selected port (default is `8080`).

## Code Structure

### Server Class (`Server.java`)

- **`ServerSocket`**: Listens on a specified port for incoming client connections.
- **Multithreading**: For each client connection, the server spawns a new thread to handle client communication.
- **Timeout Handling**: Set a server timeout to control how long it waits for a client response.
- **`PrintWriter`**: Sends messages to clients over the socket.

### Client Class (`Client.java`)

- **Threaded Client**: Spawns multiple threads to simulate multiple clients connecting to the server.
- **Socket Connection**: Each client connects to the server, sends a message, and receives a response.
- **Communication Handling**: Uses `BufferedReader` and `PrintWriter` for I/O between client and server.

### Directory Structure

```
MultiThreaded/
├── src/
│   ├── MultiThreaded/
│   │   ├── Server.java        # Server implementation
│   │   └── Client.java        # Client implementation
└── README.md                  # Documentation
```

## Setup and Running the Application

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/capybara-brain346/Multithreaded-Webserver
   cd Multithreaded-Webserver
   ```

2. **Compile the Code**:
    - Navigate to the `WebServers` directory:
      ```bash
      cd WebServers
      ```
    - Compile the classes:
      ```bash
      javac MultiThreaded/Server.java MultiThreaded/Client.java
      ```

3. **Run the Server**:
    - In one terminal, start the server:
      ```bash
      java MultiThreaded.Server
      ```

4. **Run the Client**:
    - In another terminal, start the client:
      ```bash
      java MultiThreaded.Client
      ```

    - **Expected Output**: The server should print "Connected to <client_address>" for each client connection, and each client should receive a greeting message from the server.

## How It Works

1. **Server Setup**:
    - The `Server` class listens on port `8080` and waits for client connections.
    - When a client connects, the server spawns a new thread to handle the communication for that client, allowing the server to continue listening for other incoming connections.

2. **Client Connections**:
    - The `Client` class creates multiple threads (100 by default) to simulate multiple clients connecting to the server.
    - Each client thread opens a socket to connect to the server, sends a greeting message, and then reads the server's response.

3. **Multithreading**:
    - The server uses `Runnable` and `Thread` for concurrent handling of client connections.
    - The client creates multiple threads to simulate simultaneous connection requests to the server.

## Troubleshooting

- **Connection Refused**:
    - Ensure the server is running before starting the clients.
    - Verify that the port (default is 8080) is open and not in use by another process.
    - Confirm that no firewall or network restrictions are blocking access to the port.

- **Timeout Issues**:
    - Adjust `socket.setSoTimeout(10000);` in `Server.java` if clients are disconnected prematurely.

- **Port Conflicts**:
    - If the server's port is in use by another application, change the `port` variable in both `Server.java` and `Client.java` to an available port.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue for any changes or improvements.

## License

This project is licensed under the MIT License.
