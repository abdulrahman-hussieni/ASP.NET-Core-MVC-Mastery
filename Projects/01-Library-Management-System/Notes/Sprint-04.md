# Sprint 04 — ASP.NET Core Host & Kestrel Configuration

> **Project 01 — Library Management System**

---

# 🎯 Sprint Goal

Understand how Kestrel knows where to listen and what the ASP.NET Core Host is responsible for before the application starts handling requests.

By the end of this Sprint, I should understand:

* What the ASP.NET Core Host is.
* The responsibility of the Host.
* The relationship between the Host and Kestrel.
* What `launchSettings.json` does.
* Who decides which Port Kestrel listens on.
* Why `launchSettings.json` is not required in Production.

---

# 🗺 Request Journey Overview

```text
Browser
    ↓
HTTP Request
    ↓
Kestrel Web Server
    ↓
🚧 ASP.NET Core Host
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
Kestrel
    ↓
✅ ASP.NET Core Host
```

---

# 📚 Concepts Covered

* ASP.NET Core Host
* Kestrel Configuration
* launchSettings.json
* applicationUrl
* Development vs Production Configuration

---

# ❓ The Problem

When Kestrel starts...

Who tells it to listen on Port **5001**?

Does Kestrel choose the Port by itself?

Or does another component configure it?

---

# 💡 Key Concepts

## ASP.NET Core Host

The Host is responsible for preparing the entire ASP.NET Core application before it starts serving requests.

Responsibilities include:

* Reading configuration.
* Building Dependency Injection.
* Starting Kestrel.
* Building the Middleware Pipeline.
* Managing the application lifetime.

The Host acts as the application manager.

Kestrel is only one component managed by the Host.

---

## Kestrel

Kestrel is responsible only for:

* Listening on configured URLs.
* Accepting incoming HTTP requests.
* Forwarding requests into the ASP.NET Core Pipeline.

It does **not** build the application.

It does **not** configure services.

It does **not** build the Middleware Pipeline.

---

## launchSettings.json

`launchSettings.json` is a **development configuration file**.

It usually contains:

```json
"applicationUrl": "https://localhost:5001;http://localhost:5000"
```

During development, the Host reads this configuration and instructs Kestrel to listen on those URLs.

---

## Who Chooses the Port?

During Development, the Port is commonly provided by:

* `launchSettings.json`

However, in other environments the Port may come from:

* IIS
* Docker
* Azure
* Environment Variables
* `UseUrls()` inside the application

The Host passes the final configuration to Kestrel.

---

## Host vs Kestrel

```text
ASP.NET Core Host
│
├── Read Configuration
├── Build Services
├── Configure Logging
├── Start Kestrel
├── Build Middleware Pipeline
└── Run Application
```

```text
Kestrel
│
├── Listen on Ports
├── Accept Connections
├── Receive HTTP Requests
└── Pass Requests to ASP.NET Core
```

---

# 💬 My Answers

## Question 1

### What happens if launchSettings.json is deleted?

### My Answer

I initially thought the application would stop working because the hosting configuration would be missing.

### Mentor Feedback

Good reasoning, but this is a common misconception.

`launchSettings.json` is **not required** for ASP.NET Core to run.

It is mainly used during development.

The application can still run if URLs are provided through:

* Environment Variables
* `UseUrls()`
* IIS
* Docker
* Azure

---

## Question 2

### What is the relationship between the Host and Kestrel?

### My Answer

Kestrel is a component managed by the ASP.NET Core Host.

### Mentor Feedback

Excellent.

The Host prepares the application.

Kestrel only performs one responsibility: receiving incoming HTTP requests.

---

## Question 3

### Who chooses the Port?

### My Answer

During development, the Port is usually configured in `launchSettings.json`.

### Mentor Feedback

Correct.

More generally, the Port depends on the hosting environment.

Development is only one possible scenario.

---

## Question 4

### Why are the Host and Kestrel separate?

### My Answer

Because Kestrel should remain lightweight and focused on a single responsibility, while the Host manages the rest of the application.

### Mentor Feedback

Excellent answer.

This directly reflects the **Separation of Concerns** principle introduced in Sprint 00.

---

# ⚠️ Common Misconceptions

### ❌ Misconception 1

`launchSettings.json` is required to run ASP.NET Core.

✅ Reality:

It is only a development convenience file.

---

### ❌ Misconception 2

Kestrel chooses the Port automatically.

✅ Reality:

The Host configures Kestrel using values from the hosting environment.

---

### ❌ Misconception 3

The Host and Kestrel perform the same job.

✅ Reality:

The Host prepares and manages the application.

Kestrel only handles incoming HTTP requests.

---

# 🧠 Important Notes

* The Host starts before Kestrel.
* Kestrel is managed by the Host.
* `launchSettings.json` is not used in Production.
* The hosting environment determines the final listening URLs.
* Separation of Concerns appears again in ASP.NET Core architecture.

---

# ⭐ Golden Sentences

> The Host prepares the application. Kestrel serves the application.

---

> Kestrel is a component, not the application manager.

---

> launchSettings.json is a development convenience, not a runtime requirement.

---

> Every ASP.NET Core component has a single responsibility.

---

# 🎤 Interview Questions

* What is the ASP.NET Core Host?
* What is the difference between the Host and Kestrel?
* What is `launchSettings.json` used for?
* Is `launchSettings.json` required in Production?
* Who decides which Port Kestrel listens on?
* Can Kestrel work without `launchSettings.json`?

---

# 📌 Summary

In this Sprint, I learned how ASP.NET Core prepares an application before it begins processing requests.

I now understand that the Host is responsible for configuring and starting the application, while Kestrel is responsible only for receiving HTTP requests.

I also learned that `launchSettings.json` is primarily a development tool and that the listening Port depends on the hosting environment rather than Kestrel itself.

---

# 🚀 Next Sprint

## Sprint 05 — The .NET Execution Pipeline

### Main Questions

* What happens when I execute `dotnet run`?
* What is the .NET SDK?
* What is the .NET Runtime?
* What is the CLR?
* What is the difference between Build and Run?
* How does the Host actually start?

---

# ✅ Sprint Result

* [x] Understand ASP.NET Core Host
* [x] Understand Kestrel Configuration
* [x] Understand `launchSettings.json`
* [x] Understand Development vs Production Configuration
* [x] Understand the relationship between the Host and Kestrel
* [x] Correct common misconceptions
* [x] Complete Assignment
* [x] Pass Mentor Review

**Sprint Status:** Completed ✅
