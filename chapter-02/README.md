# Chapter 02 - Networking

## Client-Server Communication in Networking
In networking, client-server communication refers to the exchange of data between a client (e.g., a web browser or mobile app) and a server (e.g., a backend API or database). This communication relies on various protocols, which define how data is transmitted over the network.

### Common Network Protocols

#### **TCP/IP (Transmission Control Protocol / Internet Protocol)**
- TCP/IP is the fundamental suite of protocols used for communication over the internet, ensuring reliable data transmission.
- TCP manages data segmentation and reassembly, ensuring packets arrive in order, while IP handles addressing and routing.
- TCP is connection-oriented, requiring a handshake before transmission. IP ensures data reaches the correct destination.
- Used in web browsing, email, VoIP, file transfers, all internet communication.

#### **SSL/TLS (Secure Sockets Layer / Transport Layer Security)**
- SSL/TLS are cryptographic protocols that encrypt data during transmission, securing communication over the internet.
- TLS uses public-key cryptography for authentication and symmetric encryption for secure data exchange.
- TLS is the modern version of SSL; SSL 2.0 and 3.0 are deprecated.
- Used in secure websites (HTTPS), email encryption, VPN connections, online banking.

#### **DNS (Domain Name System)**
- DNS translates human-readable domain names (e.g., google.com) into IP addresses.
- A recursive query is sent to a DNS resolver, which then queries authoritative servers to resolve the domain to an IP.
- Supports caching to speed up lookups, and DNSSEC enhances security by preventing spoofing.
- Used in website address resolution, email routing, distributed networks.

#### **SSH (Secure Shell)**
- SSH is a secure protocol for remote system access and file transfers.
- Uses public-key authentication and strong encryption to prevent eavesdropping.
- Commonly used for server management supports features like SSH tunneling and SCP/SFTP for file transfers.
- Uses port 22
- Used in secure remote login, system administration, encrypted file transfers.

#### **HTTP/HTTPS (Hypertext Transfer Protocol)**
- HTTP is the protocol for web communication, and HTTPS is its secure version with encryption.
- Follows a request-response model, where the client sends a request, and the server responds with data (HTML, JSON, etc.).
- HTTPS uses TLS encryption for security, preventing MITM attacks.
- HTTP uses port 80 and https uses port 443.
- Used in web browsing, API communication, secure transactions.

#### **WebSocket**
- WebSocket is a protocol for persistent, full-duplex communication between a client and server.
- After an initial handshake over HTTP, WebSocket keeps the connection open for real-time data exchange.
- More efficient than HTTP polling for low-latency applications.
- ws users port 80 and wss uses port 443.
- Used in live chat, stock market updates, real-time gaming.

#### **RPC (Remote Procedure Call)**
- RPC allows a client to execute a function on a remote server as if it were local.
- The client sends a request with the function name and parameters, and the server executes it and returns a response.
- Can be synchronous (blocking) or asynchronous (non-blocking), and gRPC (a modern RPC framework) supports TLS encryption.
- Used in microservices, distributed computing, blockchain interactions.

#### **FTP/FTPS (File Transfer Protocol)**
- FTP is a protocol for transferring files between a client and a server, while FTPS adds SSL/TLS encryption for security.
- Clients connect to an FTP server, authenticate (if required), and transfer files.
- FTP operates in active and passive modes, and FTPS ensures secure authentication and encrypted transfers.
- Used in website file uploads, data backups, enterprise file sharing.

### **SMTP (Simple Mail Transfer Protocol)**
- SMTP is the standard protocol for sending emails between mail servers.
- An email client sends messages to an SMTP server, which then relays them to the recipient’s mail server.
- SMTP is used for sending only; protocols like IMAP/POP3 handle email retrieval.
- Used in email sending, mail server communication.

#### **Protocol Comparison Table**
| Protocol   | Purpose                     | Used In                               |
|-----------|-----------------------------|--------------------------------------|
| **TCP/IP**  | Core internet communication  | Web, email, VoIP, all networking |
| **SSL/TLS** | Encrypts network traffic     | Secure websites, VPNs, banking |
| **DNS**  | Resolves domain names        | Website access, email routing |
| **SSH**   | Secure remote access        | Server login, secure file transfer |
| **HTTP**  | Web communication (insecure) | Basic websites, APIs                |
| **HTTPS** | Secure web communication     | Secure websites, APIs               |
| **WebSocket** | Real-time communication  | Chat apps, gaming, live updates     |
| **RPC**   | Remote procedure calls       | Microservices, distributed systems |
| **FTP**   | File transfer (insecure)     | Transferring files                  |
| **FTPS**  | Secure file transfer         | Secure file transfers               |
| **SMTP**  | Email sending protocol       | Sending emails, mail server communication |

