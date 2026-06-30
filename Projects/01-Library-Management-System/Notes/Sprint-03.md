# Sprint 03 — Deep Dive into Kestrel

> **Project 01 — Library Management System**

---

# 🎯 Sprint Goal

Understand how Kestrel actually works internally before learning the ASP.NET Core Request Pipeline.

The objective of this Sprint is to understand:

* What happens after running an ASP.NET Core application.
* What a Process is.
* How Kestrel starts.
* What a Port is.
* What "Listening" actually means.
* What a Socket is.
* How the browser reaches the application.

---

# 🗺 Request Journey Overview

```text
Browser
    ↓
HTTP Request
    ↓
✅ Kestrel Web Server
    ↓
ASP.NET Core Host
    ↓
Middleware Pipeline
    ↓
Endpoint Routing
    ↓
MVC
    ↓
Controller Activation
    ↓
Action Execution
    ↓
Model Binding
    ↓
Validation
    ↓
Business Logic
    ↓
Action Result
    ↓
Razor View Engine
    ↓
HTML Response
    ↓
HTTP Response
    ↓
Browser
```

---

## 📍 Current Position

```text
Browser
    ↓
HTTP Request
    ↓
✅ Kestrel Web Server
```

In this Sprint, we focus only on understanding how Kestrel receives incoming requests.

---

# 📚 Concepts Covered

* Program
* Process
* Kestrel
* Listening
* Port
* Socket
* TCP Connection (Introduction)

---

# ❓ The Problem

When we execute:

```bash
dotnet run
```

What actually happens?

Does Kestrel immediately start receiving requests?

Where does it run?

Who tells it to listen on Port 5001?

---

# 💡 Key Concepts

## Program vs Process

A **Program** is a file stored on disk.

Example:

```text
MyApplication.exe
```

A **Process** is the running instance of that program created by the Operating System.

When a program starts, the OS creates a Process that contains:

* Executable Code
* Memory
* Threads
* Handles
* Network Connections
* Other resources

Relationship:

```text
Program (.exe)
        │
        ▼
Operating System
        │
Creates
        ▼
Process
```

---

## Where Does Kestrel Run?

Kestrel is **not** a separate application.

It runs inside the ASP.NET Core Process.

```text
Operating System
        │
        ▼
ASP.NET Core Process
        │
        ├── Kestrel
        ├── ASP.NET Core Host
        ├── Middleware
        ├── Routing
        └── MVC
```

---

## What is a Port?

A Port is a logical endpoint that allows multiple applications to communicate through the same computer.

Think of it like an apartment number inside a building.

* IP Address → Building
* Port → Apartment Number

Examples:

```text
Port 80      → HTTP
Port 443     → HTTPS
Port 1433    → SQL Server
Port 5001    → ASP.NET Core
```

Only one application can listen on the same port at the same time.

---

## What Does "Listening" Mean?

When Kestrel starts, it asks the Operating System to reserve a specific Port.

After successfully binding to that Port, it enters a waiting state called **Listening**.

Example:

```text
Now listening on:
https://localhost:5001
```

This means:

> Kestrel successfully reserved Port 5001 and is ready to accept incoming network connections.

---

## What is a Socket?

A Socket is the communication endpoint used to establish a connection between two applications.

Simple analogy:

* IP Address → Building
* Port → Apartment
* Socket → The actual conversation between two people.

---

## Request Flow (Current Understanding)

```text
Browser
    │
    ▼
IP Address
    │
    ▼
TCP Connection
    │
    ▼
Port
    │
    ▼
Kestrel
```

HTTP travels over a TCP connection.

At this stage, we only need to know that TCP establishes the connection before HTTP data is exchanged.

---

# 💬 My Answers

## Question 1

### What is the difference between a Program and a Process?

### My Answer

A Program is an executable file stored on the hard disk.

A Process is the running instance of that executable after the Operating System loads it into memory.

### Mentor Feedback

Excellent.

One improvement:

A Process is more than the executable itself.

It also contains memory, threads, handles, and all runtime resources needed while the application is running.

---

## Question 2

### Why can't two applications use the same Port?

### My Answer

Just like two apartments cannot have the same apartment number in the same building, the Operating System would not know which application should receive the incoming request.

### Mentor Feedback

Excellent analogy.

The Operating System guarantees that only one application can reserve a specific port at a time.

Otherwise, incoming requests would become ambiguous.

---

## Question 3

### What does "Kestrel is listening on Port 5001" mean?

### My Answer

It means Kestrel is ready to receive incoming requests from the browser.

### Mentor Feedback

Excellent.

More precisely:

Kestrel has successfully registered itself with the Operating System on Port 5001 and is waiting for incoming TCP connections.

---

## Question 4

### Explain IP Address, Port, and Socket.

### My Answer

* IP Address identifies the device.
* Port identifies the application running on that device.
* Socket is the communication channel through which data flows between the Browser and Kestrel.

### Mentor Feedback

Excellent understanding.

Remember:

* IP → Device
* Port → Application
* Socket → Active communication endpoint

---

# 🧠 Important Notes

* A Process is created by the Operating System.
* Kestrel runs inside the ASP.NET Core Process.
* A Port identifies the application.
* Only one application can listen on a port at a time.
* Listening means waiting for incoming TCP connections.
* HTTP is built on top of TCP.

---

# ⭐ Golden Sentences

> A Program is stored on disk. A Process is a running Program.

---

> Kestrel is part of the ASP.NET Core Process, not a separate application.

---

> A Port identifies an application, not a computer.

---

> Listening means waiting for incoming network connections.

---

> HTTP communication starts only after a TCP connection is established.

---

# 🎤 Interview Questions

* What is the difference between a Program and a Process?
* What is a Port?
* What does "Now listening on..." mean?
* Can two applications listen on the same port?
* Does Kestrel run as a separate application?
* What is a Socket?
* Does HTTP work directly over the network?

---

# 📌 Summary

In this Sprint, I learned what happens immediately after executing an ASP.NET Core application.

I now understand:

* The difference between a Program and a Process.
* That Kestrel runs inside the ASP.NET Core Process.
* How Kestrel reserves a Port.
* What Listening actually means.
* The relationship between IP Address, Port, and Socket.
* That HTTP communication begins only after a TCP connection has been established.

This knowledge prepares me to understand how the Operating System forwards incoming requests to Kestrel.

---

# 🚀 Next Sprint

## Sprint 04 — Kestrel Configuration & ASP.NET Core Host

### Main Questions

* Who chooses Port 5001?
* What is `launchSettings.json`?
* What is the ASP.NET Core Host?
* How does Kestrel know which URLs to listen on?
* What happens before the Middleware Pipeline starts?

---

# ✅ Sprint Result

* [x] Understand Program vs Process
* [x] Understand Kestrel Internals
* [x] Understand Ports
* [x] Understand Listening
* [x] Understand Sockets
* [x] Understand the first stage of network communication
* [x] Complete Assignment
* [x] Pass Mentor Review

**Sprint Status:** Completed ✅
