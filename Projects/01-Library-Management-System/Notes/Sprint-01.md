# Sprint 01 — HTTP & Web Fundamentals

> **Project:** Library Management System  
> **Phase:** Request Lifecycle Foundations  
> **Sprint Goal:** Understand everything that happens from the moment a user presses **Enter** in the browser until the HTTP Request leaves the client and starts its journey toward ASP.NET Core.

---
# 🎯 Sprint Objectives
    - Explain how communication starts between a Browser and a Web Server.
    - Understand the structure of a URL.
    - Understand how the Browser prepares an HTTP Request.
    - Read and analyze any HTTP Request.
    - Read and analyze any HTTP Response.
    - Understand HTTP Methods.
    - Understand HTTP Headers.
    - Understand HTTP Body.
    - Understand HTTP Status Codes.
    - Inspect HTTP traffic using Chrome DevTools.
    - Prepare for entering the ASP.NET Core Request Pipeline.

---
# 🗺 Request Journey

```text
                                                        User
                                                            │
                                                            ▼
                                                        Browser
                                                            │
                                                            ▼
                                                        URL
                                                            │
                                                            ▼
                                                        Browser Internal Work
                                                            │
                                                            ▼
                                                        HTTP Request
                                                            │
                                                            ▼
                                                        Internet
                                                            │
                                                            ▼
                                                        Kestrel
                                                            │
                                                            ▼
                                                        ASP.NET Core
```

> This Sprint covers everything from **User** until the request reaches **Kestrel**.

---
# Lesson 01 — What Happens When I Press Enter?
---

## 🎯 Goal
    Understand the complete journey that starts after pressing **Enter** inside the Browser.

---

## 💡 Concepts

    Typing a URL inside the Browser does **not** send the request directly to ASP.NET Core.
    
    Instead, the Browser starts preparing an HTTP Request.
    
    The Request must travel through several stages before reaching our application.

---

    ## 🌍 Beyond ASP.NET Core
      Before reaching ASP.NET Core, every Request passes through technologies like:
          - DNS
          - TCP
          - TLS
      These belong to Networking rather than ASP.NET Core.

---

## 🧠 Think Like an Engineer

When you press **Enter**, does the Browser immediately contact ASP.NET Core?  No.

Many operations happen before any communication with the server begins.

---
# Lesson 02 — URL Fundamentals
---

## 🎯 Goal
    Understand every component inside a URL and why each part exists.
---
Example:

```text
    https://localhost:5001/books/15?page=2&sort=name
```

A URL is composed of multiple parts.

| Part | Example |
|------|----------|
| Protocol | https |
| Host | localhost |
| Port | 5001 |
| Path | /books/15 |
| Query String | ?page=2&sort=name |

---

### Protocol
    Defines the communication rules between the Client and the Server.
    Examples:
    
    - HTTP
    - HTTPS
    
    HTTPS = HTTP + TLS Encryption.

---

### Why do we need a Protocol?
    Without common communication rules:
    
    - Browsers couldn't communicate with Servers.
    - Every company would invent its own communication format.
    - The Web would not be standardized.
---

### Host
    Specifies which Server should receive the Request.

Examples:
```text
    google.com
    
    github.com
    
    localhost
```

---

## Domain vs Host

    - Domain is the registered website name.
    
    - Host identifies the destination machine.

In many URLs they appear identical, but they are not conceptually the same.

---

### FQDN (Fully Qualified Domain Name)

Example:

    www.google.com
    
    It represents the complete domain hierarchy.
--

### localhost

    `localhost` always refers to your own computer.

Equivalent IP Address:

```text
127.0.0.1
```
---

### IP Address

    Every device connected to a network has an address.

Example:

```text
192.168.1.10
```

Domain names exist because remembering IP addresses is difficult.

---

### Port

    The Port identifies which application should receive the Request.

Example:

```text
https://localhost:5001
```

5001 identifies the ASP.NET Core application listening on that machine.

---

### Why is Port needed?

    One computer may run: All share the same IP Address. Ports distinguish between them.

---
### Path

Represents the Resource requested from the Server.

Examples:

```text
    /books
    
    /books/15
    
    /api/products
```

---

### Route vs Path

    Path belongs to the URL.
    
    Route is how ASP.NET Core matches that Path to an Endpoint.
    
    We'll study Routing later.

---

### Query String

Extra information sent with the Request.

Example:

```text
?page=2&sort=name
```

Often used for:

- Filtering
- Searching
- Sorting
- Pagination

---

### URL Encoding

Some characters cannot appear directly inside a URL.

Example:

Space

↓

```text
%20
```

Example:

```text
Clean Code
```

becomes

```text
Clean%20Code
```

---

### Reserved Characters

    Characters like: [ ? & # / ]
    
    already have meanings inside URLs.
    
    They must be encoded when used as data.

---

### URI vs URL vs URN

    URI : General identifier.
    
    ↓
    
    URL : Identifier + Location.
    
    ↓
    
    URN : Identifier without Location.

For Web Development we mainly work with URLs.

---

### Absolute URL : Contains everything.

    https://localhost:5001/books    
---

### Relative URL : Depends on the current page.
    
    /books
---

### Base URL : The common starting point.

    https://localhost:5001

---

### Virtual Directory (Introduction) : Some Servers host multiple applications under one Domain.

    https://company.com/hr
We'll revisit this during IIS Deployment.



Now that the Browser understands the URL...

**What happens inside the Browser before sending the HTTP Request?**
