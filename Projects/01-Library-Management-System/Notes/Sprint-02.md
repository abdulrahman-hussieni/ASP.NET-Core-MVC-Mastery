# 🚧 Sprint 02 — Kestrel & Web Hosting Fundamentals

> **Goal:** Understand how ASP.NET Core applications are hosted and why Kestrel exists.

---

# 📚 Lesson 01 — What is a Server?

        A **Server** is a computer or software whose job is to provide services to other computers called **Clients**.

        The Server waits for incoming Requests, processes them, and returns Responses.

        Examples:
        
        - File Server
        - Database Server
        - Mail Server
        - Web Server

---

## Client vs Server
        **The Client:** starts the communication.
        **The Server:** receives the Request and sends back the Response.
```text
          Request
Client   ------->    Server
         <-------
          Response 
```
---

## Can my Laptop become a Server?        Yes.

When you run:
```bash
dotnet run
```
        Your computer starts **listening for incoming Requests** ,At that moment, your machine becomes a **Server**.
---

## Physical vs Virtual Server
                A **Physical Server** is a real machine located in a data center.
                
                A **Virtual Server** is a virtual machine running on physical hardware using virtualization technology.
                
                Most Cloud providers use Virtual Servers.
---

# 📚 Lesson 02 — What is a Web Server?

## What is a Web Server?
        A **Web Server** is a Server specialized in handling HTTP and HTTPS communication.
        
        Its primary job is to receive HTTP Requests and return HTTP Responses.
---
## Responsibilities of a Web Server
        - Listen for HTTP Requests.
        - Accept incoming Connections.
        - Parse HTTP Requests.
        - Send HTTP Responses.
        - Serve Static Files.

Some Web Servers also provide:
        
        - SSL Termination
        - Logging
        - Compression
        - Load Balancing

---
## Popular Web Servers
        - IIS
        - Nginx
        - Apache
        - Kestrel

> Kestrel is the default Web Server for ASP.NET Core.

---

# 📚 Lesson 03 — Static vs Dynamic Websites

## Static Website
       - A Static Website contains fixed files.
        -Example:
                - index.html
                - style.css
                - logo.png
        - Every visitor receives the same content.
        - No database or server-side processing is required.
---
## Dynamic Website
        - A Dynamic Website generates content during runtime.
         - The response may change depending on:
                - Database data
                - Logged-in user
                - Permissions
                - Time
                - Business logic
        - ASP.NET Core MVC applications are Dynamic Websites.
---

# 📚 Lesson 04 — Hosting Fundamentals
        - Hosting means making your application available to receive Requests.
        - Without Hosting, the application is just files stored on disk.
---
## Types of Hosting

### Local Hosting : The application runs on your own machine.
        Example:
                dotnet run
---
### Production Hosting : The application runs on a public Server accessible by users.
---
### Cloud Hosting : The application runs on cloud platforms such as:
        - Microsoft Azure
        - AWS
        - Google Cloud
---
## Deployment vs Hosting
        **Deployment** means publishing your application.
        **Hosting** means running the application and waiting for Requests.

---
# 📚 Lesson 05 — Why Kestrel Exists

## Before ASP.NET Core
        ASP.NET Framework applications depended entirely on IIS.
                
                Browser ----> IIS ----> ASP.NET Framework

> This limited applications to Windows.
---
## The Problem
        - Windows-only hosting.
        - Tight dependency on IIS.
        - Limited cross-platform support.
---
## Microsoft's Solution

Microsoft built a **lightweight**, **cross-platform Web Server** called **Kestrel**.
        Now ASP.NET Core applications can run on:
        - Windows
        - Linux
        - macOS
     without depending on IIS.

---
## Advantages of Kestrel
        - High Performance
        - Lightweight
        - Cross Platform
        - Open Source
---

# 📚 Lesson 06 — IIS + Kestrel
**In Production**, the Request usually follows this path:
```text
        Browser ----> IIS ----> Kestrel ----> ASP.NET Core
```

---

## IIS Responsibilities
        - SSL Termination
        - Load Balancing
        - Static File Serving
        - Security
        - Reverse Proxy
---
## Kestrel Responsibilities
        - Receive Requests from IIS.
        - Create the HttpContext.
        - Pass the Request into ASP.NET Core.
        - Return the Response back to IIS.

---        

## Why Not Use IIS Alone?
        - ASP.NET Core no longer runs inside IIS.
        - Kestrel is responsible for executing the ASP.NET Core application.
        - IIS mainly acts as a Reverse Proxy.
---

# 📚 Lesson 07 — Nginx + Kestrel  [ Linux hosting. ]

On Linux, IIS is usually replaced by Nginx.

The Request flow becomes:

```text
        Browser ----> Nginx ----> Kestrel ----> ASP.NET Core
```
---

## Nginx Responsibilities
        - Reverse Proxy
        - SSL Termination
        - Static File Serving
        - Load Balancing
Kestrel still executes the ASP.NET Core application.

---
# 📚 Lesson 08 — Development vs Production
        Understand how hosting changes between Development and Production.
---
## Development

During development:

```text
Browser ----> Kestrel ----> ASP.NET Core
```
No IIS or Nginx is required.

---
## Production
```text
Browser ----> IIS / Nginx ----> Kestrel ----> ASP.NET Core
```
The Reverse Proxy handles infrastructure concerns, while Kestrel executes the application.

---

# 🧪 Mini Labs

- Run an ASP.NET Core project using `dotnet run`.
- Observe the "Now listening on..." message.
- Open the application in your Browser.
- Identify whether IIS is involved.
- Compare the Development and Production architectures.

---
