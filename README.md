# UNIX & Internet Domain Socket Chat Applications

This project includes two types of **client-server chat applications** implemented in C:
- **UNIX Domain Socket Chat** (local communication)
- **Internet Domain Socket Chat (TCP/IP)** (network communication)

Both applications allow real-time bi-directional messaging between a server and a client.

---

## 📌 Features
- **UNIX Domain Sockets**: Local communication using `AF_UNIX`.
- **Internet Domain Sockets (TCP/IP)**: Network communication using `AF_INET`.
- **Bi-directional messaging** between client and server.
- **Graceful termination** upon client disconnection.
- **Simple, interactive chat interface**.

---

## 🔧 Prerequisites
- **Linux/macOS** (or **Windows with WSL**)
- **GCC compiler** installed
- Basic knowledge of **sockets and networking**

---

## 📦 Compilation
Compile both server and client programs:
```sh
# For UNIX Domain Socket Chat
gcc unix_server.c -o unix_server
gcc unix_client.c -o unix_client

# For TCP/IP Socket Chat
gcc tcp_server.c -o tcp_server
gcc tcp_client.c -o tcp_client
```

---

## 🚀 Usage
### **UNIX Domain Socket Chat**
#### Start the Server
```sh
./unix_server
```
By default, it listens on `/tmp/unix_socket`.

#### Start the Client
```sh
./unix_client
```
This connects the client to the server.

#### Example Session
```
Server:
$ ./unix_server
Waiting for connections...
Client connected!
Client: Hello, Server!
You: Hi, Client!
```

```
Client:
$ ./unix_client
Connected to server. Type 'exit' to quit.
You: Hello, Server!
Server: Hi, Client!
```

#### Cleanup
After running the server, remove the socket file:
```sh
rm -f /tmp/unix_socket
```

---

### **Internet Domain Socket Chat (TCP/IP)**
#### Start the Server
```sh
./tcp_server
```
This starts the server on **port 12345**.

#### Start the Client
```sh
./tcp_client
```
This connects to the server at **127.0.0.1:12345**.

#### Example Session
```
Server:
$ ./tcp_server
Waiting for connections...
Client connected!
Client: Hello, Server!
You: Hi, Client!
```

```
Client:
$ ./tcp_client
Connected to server. Type 'exit' to quit.
You: Hello, Server!
Server: Hi, Client!
```

---

## 📜 Code Explanation
### `unix_server.c`
- Creates a **UNIX domain socket**.
- Binds it to `/tmp/unix_socket`.
- Waits for a client connection.
- Reads and sends messages.
- Closes the socket on exit.

### `unix_client.c`
- Connects to the **UNIX domain socket**.
- Sends and receives messages.
- Closes the connection on `exit` command.

### `tcp_server.c`
- Creates a **TCP socket** and binds it to **port 12345**.
- Waits for client connections.
- Reads and sends messages.
- Closes the socket on client disconnect.

### `tcp_client.c`
- Connects to the **server at 127.0.0.1:12345**.
- Sends and receives messages.
- Closes the connection on `exit` command.

---

## 🛠️ Troubleshooting
### **Permission Denied for UNIX Socket File**
Run:
```sh
chmod 666 /tmp/unix_socket
```

### **Port Already in Use (TCP Server)**
If you see `Bind failed: Address already in use`, run:
```sh
sudo netstat -tulnp | grep :12345  # Find the process using port 12345
sudo kill -9 <PID>                 # Replace <PID> with the actual process ID
```

---

## 👥 Authors
[Deepika Reddy-23071A3228, Akshaya-23071A3227, Lavanya-24075A3201, Sravanthi-23071A3215]

This project was developed for learning and demonstration purposes.

---

## 📜 License
This project is open-source and available under the **MIT License**.

Feel free to **contribute**, **open issues**, or **fork** this project!
