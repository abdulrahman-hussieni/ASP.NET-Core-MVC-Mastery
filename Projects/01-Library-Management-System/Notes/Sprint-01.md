# Sprint 01 — HTTP Request

> **Project 01 — Library Management System**

---
# 🎯 Sprint Goal

- Understand what happens immediately after pressing **Enter** in the browser.
  
- The objective of this Sprint is to understand how communication starts between the browser and the server before ASP.NET Core MVC becomes involved

---
# 📚 Concepts Covered

* Browser
* URL
* HTTP
* HTTP Request
* HTTP Response
* Request Lifecycle (Introduction)

---
# ❓ The Problem

When a user types:

```text
https://localhost:5001/books
```

and presses **Enter**...

What actually happens?

Does the request go directly to the Controller?

The answer is **No**.

Before reaching MVC, the request must travel through several stages.

---
# 🗺 Request Journey Overview


> **Note**
> At this stage, I am **not expected to understand every step**.
> This diagram is only a roadmap.
> During the upcoming Sprints, every single box below will become a complete lesson until I fully understand the entire Request Lifecycle.

```text
Browser
    ↓
HTTP Request
    ↓
Kestrel Web Server
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
## 📍 Current Position

```text
Browser
    ↓
✅ HTTP Request
```

Everything below **HTTP Request** will be explored in detail throughout the upcoming Sprints.

---
# 💡 Key Idea

The browser does not communicate directly with MVC.

Instead, it sends an **HTTP Request**.

### HTTP:
    is a communication protocol that defines the rules both the browser and the server must follow.

Without a common protocol, communication between different browsers and different servers would not be possible.

---
# 🧠 Important Notes

* HTTP is a communication protocol => defines communication rules.
* HTTP itself is **not responsible for security**.
* HTTPS is HTTP protected by TLS encryption.
* Every HTTP Request follows a journey before reaching its final destination.

---

# 💬 My Answers

## Question 1

### Why doesn't the request go directly to the Controller?

### My Answer

ASP.NET Core is much larger than MVC.

MVC is only one part of ASP.NET Core.

The request must first enter ASP.NET Core so it can be directed to the correct destination instead of randomly reaching a Controller.

This organization makes the application more efficient and scalable.

Not every request should go to MVC.

Some requests may be for:

* Static Files
* CSS
* JavaScript
* Images
* APIs
* SignalR

ASP.NET Core decides where the request should go.

---

## Question 2

### Why do we need HTTP?

### My Answer

HTTP defines the communication rules between the browser and the server.

Without these rules, every browser and every server would communicate differently, making communication unreliable.

HTTP is responsible for communication.

HTTPS is responsible for secure communication.

Always distinguish between communication and security.


---


# 🎤 Interview Questions

### Why doesn't every HTTP Request go directly to a Controller?

### What is HTTP?

### What is the difference between HTTP and HTTPS?

### Is MVC responsible for receiving the request?

### Why is MVC only one part of ASP.NET Core?

---
**Question:**

> Who actually receives the HTTP Request first?????????? next sprint 

---

# ✅ Sprint Result

* [x] Understand HTTP
* [x] Understand HTTP Request
* [x] Understand HTTP Response
* [x] Understand the role of the Browser
* [x] Begin understanding the Request Lifecycle
* [x] Complete Assignment
* [x] Pass Mentor Review

**Sprint Status:** Completed ✅
