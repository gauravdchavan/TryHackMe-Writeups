# TryHackMe – Client-Server Basics

> **Platform:** TryHackMe
> **Path:** Pre Security → Computer Fundamentals
> **Room:** Client-Server Basics
> **Difficulty:** Easy
> **Status:** ✅ Completed

---

## 📌 Overview

The **Client-Server model** is a fundamental concept in networking. It explains how one computer (the **client**) requests a service or resource from another computer (the **server**).

This room covers:

* Client and Server
* Request and Response
* Protocols
* Ports
* IP Addresses
* DNS
* HTTP/HTTPS
* URLs
* GET requests
* Web communication

TryHackMe's official room describes these as the main learning objectives.

---

# 1. Introduction

In the early days of computing, computers mostly worked independently. As networks developed, computers began communicating with each other to share information and resources.

Networks such as **ARPANET, CYCLADES, NPL, and NSFNET** helped establish the foundations of the modern Internet.

The Client-Server model allows computers to specialize in providing and consuming services.

### Key Idea

```text
Client → Request → Server
Client ← Response ← Server
```

---

# 2. Client-Server Model

## 👤 Client

A **client** is a device or application that requests a service from a server.

Examples:

* Web browser
* Mobile application
* Email client
* FTP client

**Important:** The client normally initiates the communication.

## 🖥️ Server

A **server** is a computer or system that provides services or resources to clients.

Examples:

* Web server
* Database server
* File server
* DNS server
* Mail server

---

# 3. Pizza Delivery Analogy 🍕

TryHackMe uses a pizza delivery example to explain the Client-Server model.

| Pizza Example      | Computer Networking    |
| ------------------ | ---------------------- |
| Alice              | Client/User            |
| Bob                | Protocol/Communication |
| Luigi's Pizza      | Server                 |
| Pizza order        | Request                |
| Pizza              | Response               |
| Pizza shop door    | Port                   |
| GPS                | DNS                    |
| Pizza shop address | IP Address             |

### Example

```text
Client
  ↓
Request
  ↓
Server
  ↓
Process Request
  ↓
Response
  ↓
Client
```

This analogy makes it easier to understand how computers communicate.

---

# 4. Request and Response

### Request

A **request** is sent by the client to ask the server for a resource or service.

Example:

```text
Browser → Request → Web Server
```

### Response

A **response** is sent by the server after processing the client's request.

Example:

```text
Web Server → Response → Browser
```

If the request is invalid or the resource does not exist, the server may return an error response.

---

# 5. Protocol

A **protocol** is a set of rules that defines how computers communicate.

A protocol specifies:

* Commands that can be used
* Request structure
* Syntax
* Expected responses
* How errors are handled

### Examples

* HTTP
* HTTPS
* DNS
* FTP
* SSH
* TCP
* UDP

### Simple Definition

> **Protocol = Rules for communication between systems**

---

# 6. Port

A **port** identifies a specific service running on a system.

A server can run multiple services simultaneously, with different services using different ports.

### Example

```text
Server
 ├── Port 22  → SSH
 ├── Port 80  → HTTP
 ├── Port 443 → HTTPS
 └── Port 53  → DNS
```

### TryHackMe Question

**What do we use to identify a specific service on a server?**

**Answer:** `Port`

---

# 7. IP Address

An **IP address** identifies the network location/address of a device.

Example:

```text
192.168.1.10
```

Servers can be accessed using their IP addresses.

### TryHackMe Question

**What do we call the address of a server?**

**Answer:** `Internet Protocol Address`

---

# 8. DNS

**DNS = Domain Name System/Service**

DNS translates human-readable domain names into IP addresses.

### Example

```text
tryhackme.com
      ↓
     DNS
      ↓
IP Address
```

Instead of remembering an IP address, users can use a domain name such as:

```text
tryhackme.com
```

### Easy Analogy

```text
DNS = GPS for the Internet
```

The pizza analogy compares DNS to a GPS that converts a known name into a destination address.

---

# 9. Web Communication

Web browsers communicate with web servers using:

* **HTTP** – Hypertext Transfer Protocol
* **HTTPS** – HTTP Secure

HTTP/HTTPS follows the Client-Server model.

```text
Browser
(Client)
   │
   │ HTTP/HTTPS Request
   ↓
Web Server
   │
   │ HTTP/HTTPS Response
   ↓
Browser
```

HTTP is **stateless**, meaning each request is handled independently by the protocol itself. Websites can still maintain sessions using mechanisms such as cookies or tokens.

---

# 10. URL

A **URL (Uniform Resource Locator)** identifies a resource on the web.

Example:

```text
https://www.iamlearning.thm/contact
```

Breakdown:

```text
https://
   │
   └── Scheme

www.iamlearning.thm
   │
   └── Host

/contact
   │
   └── Path
```

### Important URL Components

| Component | Meaning                     |
| --------- | --------------------------- |
| Scheme    | Communication protocol      |
| Host      | Server/domain name          |
| Path      | Requested resource/location |

---

# 11. Scheme

The **scheme** specifies the protocol being used.

Examples:

```text
http
https
ftp
```

For:

```text
https://www.iamlearning.thm/contact
```

The scheme is:

```text
https
```

---

# 12. Host

The **host** identifies the server/domain being accessed.

For:

```text
https://www.iamlearning.thm/contact
```

The host is:

```text
www.iamlearning.thm
```

### TryHackMe Questions

**What would be the host in the following URL?**

```text
https://www.iamlearning.thm/contact
```

**Answer:**

```text
www.iamlearning.thm
```

**What would be the scheme?**

**Answer:**

```text
https
```

---

# 13. HTTP GET Method

**GET** is an HTTP method used to retrieve a resource from a server.

Example:

```http
GET /index.php HTTP/1.1
```

The browser automatically creates HTTP requests when you visit websites.

### Basic Flow

```text
Browser
   ↓
GET Request
   ↓
Web Server
   ↓
200 OK
   ↓
Web Page
```

TryHackMe demonstrates this by using browser Developer Tools and the **Network** tab to inspect GET requests.

---

# 14. HTTP Request

An HTTP request is sent from the client to the server.

Example:

```http
GET /index.html HTTP/1.1
Host: example.com
```

Important parts include:

* HTTP method
* Requested path
* HTTP version
* Headers
* Optional body

---

# 15. HTTP Response

After processing the request, the server sends an HTTP response.

Example:

```text
HTTP/1.1 200 OK
```

The response contains information such as:

* Status code
* Response headers
* Response body

### Common Status Code

```text
200 OK
```

means the request was successful.

---

# 16. Browser Developer Tools

The room demonstrates inspecting web communication using browser Developer Tools.

### Steps

1. Open the browser.
2. Open Developer Tools using `F12`.
3. Select the **Network** tab.
4. Reload the webpage.
5. Select a request.
6. Inspect its details.

You can observe information such as:

```text
Scheme
Host
Filename/Path
Address
Status
Response
```

This is an important skill for cybersecurity and web security because it helps you understand what is happening between a browser and a web server.

---

# 🎯 Important Concepts to Remember

```text
Client
   ↓
Sends Request
   ↓
Protocol
   ↓
Server
   ↓
Processes Request
   ↓
Sends Response
   ↓
Client
```

### Quick Revision

| Concept    | Meaning                               |
| ---------- | ------------------------------------- |
| Client     | Requests a service                    |
| Server     | Provides a service                    |
| Request    | Client → Server                       |
| Response   | Server → Client                       |
| Protocol   | Rules of communication                |
| Port       | Identifies a service                  |
| IP Address | Address of a device/server            |
| DNS        | Resolves domain names to IP addresses |
| HTTP       | Web communication protocol            |
| HTTPS      | Secure HTTP                           |
| URL        | Address of a web resource             |
| GET        | Retrieves a resource                  |
| Host       | Server/domain being accessed          |
| Scheme     | Protocol used in a URL                |

---

# 📝 TryHackMe Answers

### Task 2 – Pizza Delivery

**Q1. What do we use to identify a specific service on a server?**

```text
Port
```

**Q2. What do we call the address of a server?**

```text
Internet Protocol Address
```

### Task 3 – Web Communication in Practice

**Q1. What would be the host in this URL?**

```text
https://www.iamlearning.thm/contact
```

```text
www.iamlearning.thm
```

**Q2. What would be the scheme?**

```text
https
```

These answers are documented in multiple walkthroughs of the room and align with the room's concepts.

---

# 🔐 Cybersecurity Relevance

Understanding the Client-Server model is important before learning:

* Network security
* Web security
* HTTP attacks
* Burp Suite
* Nmap
* Wireshark
* Web application penetration testing
* API security
* SOC monitoring

When analysing network traffic, you need to understand **who is communicating, which service is being accessed, which port is used, which protocol is involved, and what request/response is exchanged.**

---

# 🚀 Key Takeaways

1. **Client** requests a service.
2. **Server** provides the service.
3. **Protocols** define communication rules.
4. **Ports** identify specific services.
5. **IP addresses** identify network locations.
6. **DNS** translates domain names into IP addresses.
7. **HTTP/HTTPS** are used for web communication.
8. **GET** is used to retrieve resources.
9. A URL contains components such as **scheme, host, and path**.
10. Browser Developer Tools can be used to inspect HTTP requests and responses.

---

## ✅ Room Status

**Client-Server Basics — Completed ✔️**

This room provides the foundation needed to understand how clients communicate with servers across networks and the web.

