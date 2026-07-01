# Sprint 00 — Why ASP.NET Core MVC?

> Phase 0 — The Complete Request Lifecycle

---

# 🎯 Sprint Goal
 We will learn:
    - Why MVC exists.
    - Why ASP.NET Core was introduced.
    - The difference between Development and Production hosting.
    - The complete ASP.NET Core Request Lifecycle.

---

# 🖼 Request Lifecycle Overview

<p align="center">
    <img src="../Imags/Sprint-00.png" width="100%">
</p>

---

# 📚 Topics
    - Separation of Concerns
    - ASP.NET Framework vs ASP.NET Core
    - Development vs Production
    - IIS
    - Kestrel
    - Reverse Proxy
    - Request Lifecycle Overview
---

# 1️⃣ Why MVC?

    # ❓ The Problem
        Imagine building a website where everything exists inside one file:
          * HTML
          * CSS
          * JavaScript
          * C#
          * SQL Queries
          * Validation
          * Business Logic
Without MVC, everything would be placed in one location:

- UI
- Business Logic
- Database
- Validation
- Authentication

As the application grows, maintaining it becomes difficult.

MVC solves this by separating responsibilities.

---

# 2️⃣ Separation of Concerns

MVC divides the application into three parts.

### Model

Responsible for:

- Data
- Business Rules
- Database

---

### View

Responsible for:

- User Interface
- HTML
- Display

---

### Controller

Responsible for:

- Receiving Requests
- Calling Business Logic
- Returning Responses

---

# 3️⃣ ASP.NET Framework vs ASP.NET Core

### ASP.NET Framework

```text
                                          Browser
                                              │
                                          HTTP Request
                                              │
                                          IIS
                                              │
                                          ASP.NET MVC
                                              │
                                          Controller
                                              │
                                          View
                                              │
                                          Browser
```
---

### ASP.NET Core (Development)

  ```text
                                          Browser
                                              │
                                          HTTP Request
                                              │
                                          Kestrel
                                              │
                                          ASP.NET Core
                                              │
                                          Browser
  ```                                    
---

### ASP.NET Core (Production)

 ```text
                                          Browser
                                              │
                                          HTTP Request
                                              │
                                          IIS / Nginx
                                              │
                                          Reverse Proxy
                                              │
                                          Kestrel
                                              │
                                          ASP.NET Core
                                              │
                                          Browser
 ```
                                          
---

# 4️⃣ The Complete Request Lifecycle

Throughout this Bootcamp, we will follow the Request step by step.

 ```text
                                        Browser
                                            │
                                        HTTP Request
                                            │
                                        Kestrel
                                            │
                                        HttpContext
                                            │
                                        Middleware Pipeline
                                            │
                                        Endpoint Routing
                                            │
                                        Controller Activation
                                            │
                                        Action Execution
                                            │
                                        Model Binding
                                            │
                                        Model Validation
                                            │
                                        Business Logic
                                            │
                                        Action Result
                                            │
                                        Razor View Engine
                                            │
                                        HTML Response
                                            │
                                        HTTP Response
                                            │
                                        Browser
```

---

# ⭐ Key Takeaways

- MVC separates responsibilities.
- ASP.NET Core uses Kestrel as its web server.
- In production, IIS or Nginx usually works as a Reverse Proxy.
- Every Request follows the same lifecycle.

---
