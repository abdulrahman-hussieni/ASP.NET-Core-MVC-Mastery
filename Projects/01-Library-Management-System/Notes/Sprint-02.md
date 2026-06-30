# Sprint 02 — Web Foundations

> **Project 01 — Library Management System**

---

# 🎯 Sprint Goal

Build a strong foundation before learning Kestrel and the ASP.NET Core Request Pipeline.

The objective of this Sprint is to understand the basic building blocks of every web application:

* Server
* Web Server
* Hosting
* IIS
* Kestrel
* Reverse Proxy
* ASP.NET Core Framework

Without understanding these concepts, it is impossible to fully understand the Request Lifecycle.

---

# 🗺 Request Journey Overview

```text
Browser
    ↓
HTTP Request
    ↓
❓ Kestrel Web Server
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
🚧 Web Foundations
```

Before understanding Kestrel, we first need to understand the environment in which it works.

---

# 📚 Concepts Covered

* Server
* Web Server
* Hosting
* IIS
* Kestrel
* Reverse Proxy
* ASP.NET Core Framework

---

# ❓ The Problem

When an HTTP Request leaves the browser...

Who receives it?

Many developers answer:

* ASP.NET Core
* MVC
* Controller

None of these answers are completely correct.

To understand the correct answer, we first need to understand what a Server and a Web Server actually are.

---

# 💡 Key Concepts

## What is a Server?

A Server is **not a special computer**.

A Server is simply a program whose job is to wait for requests and respond to them.

The same physical computer can act as:

* A Client
* A Server

depending on the application running on it.

---

## What is a Web Server?

A Web Server is a Server that understands HTTP and HTTPS.

Its primary responsibilities are:

* Listen for incoming requests.
* Accept network connections.
* Receive HTTP Requests.
* Forward requests to the appropriate application.

A Web Server does **not** contain business logic.

---

## What is Hosting?

Hosting means running an application so it becomes available to receive incoming requests.

When an ASP.NET Core application starts, it becomes "hosted" and is ready to accept traffic.

---

## IIS

**Internet Information Services (IIS)** is Microsoft's traditional Web Server.

It was the primary Web Server used with ASP.NET Framework.

Characteristics:

* Runs only on Windows.
* Manages websites and applications.
* Supports Windows Authentication.
* Handles HTTPS certificates.
* Provides logging and process management.

Traditional architecture:

```text
Browser
    ↓
IIS
    ↓
ASP.NET Framework
    ↓
MVC
```

---

## Why Was Kestrel Created?

Microsoft wanted ASP.NET Core to run everywhere:

* Windows
* Linux
* macOS
* Docker
* Cloud Platforms

Since IIS only works on Windows, a new cross-platform Web Server was required.

That Web Server is **Kestrel**.

---

## Kestrel

Kestrel is Microsoft's modern, cross-platform Web Server for ASP.NET Core.

Its primary responsibilities are:

* Listen on ports.
* Accept HTTP connections.
* Receive incoming requests.
* Forward requests to the ASP.NET Core application.

Development architecture:

```text
Browser
    ↓
Kestrel
    ↓
ASP.NET Core
```

---

## Reverse Proxy

In production environments, Kestrel is often placed behind another Web Server such as IIS.

Architecture:

```text
Browser
    ↓
IIS
    ↓
Kestrel
    ↓
ASP.NET Core
```

In this configuration:

* IIS receives requests from the Internet.
* IIS performs infrastructure-related tasks.
* IIS forwards requests to Kestrel.
* Kestrel executes the ASP.NET Core application.

This forwarding process is called a **Reverse Proxy**.

---
Reverse Proxy (IIS + Kestrel)
في بيئات الإنتاج (Production)، كستريل (Kestrel) مش بيقف لوحده في الوش قدام الإنترنت مباشرة. بنحط قبله ويب سيرفر تاني زي IIS (أو Nginx على لينكس) يشتغل كـ Reverse Proxy.

❓ ليه وجع الدماغ ده؟ ما نستخدمش كستريل لوحده ليه؟
كستريل اتصمم عشان يكون سريع جداً وخفيف (Lightweight) وعابر للمنصات (Cross-platform). وعشان يفضل بالسرعة دي، ما حطوش فيه ميزات إدارة السيرفرات المعقدة.

الـ IIS هنا بيشتغل كـ موظف استقبال وأمن بيحمي الكستريل وبيشيل عنه الشغل الإداري:

تأمين وحماية أقوى (Security): الـ IIS بيصد الهجمات الخبيثة (زي DDoS attacks) قبل ما توصل لتطبيقك.

إدارة شهادات الأمان (SSL/TLS Termination): الـ IIS هو اللي بيقك تشفير الـ HTTPS وبيدي الطلب للكستريل "جاهز"، فبيوفر مجهود البروسيسور لتطبيقك.

مشاركة المنفذ (Port Sharing): لو عندك 5 مواقع على نفس السيرفر، كلهم عاوزين يشتغلوا على بورت 443. الكستريل ما يقدرش يشارك البورت، لكن الـ IIS بيستلم كله ويوزع لكل كستريل حاجته.

إعادة التشغيل التلقائي (Process Management): لو الكود بتاعك حصل فيه كراش (Crash) ومات، الـ IIS بيصحيه ويعيد تشغيله فوراً من غير ما الموقع يقع.

---
## ASP.NET Core Framework

ASP.NET Core is **not** a Web Server.

It is an Application Framework that provides everything needed to build web applications.

It includes features such as:

* Middleware Pipeline
* Routing
* MVC
* Web API
* Razor Pages
* SignalR
* Authentication
* Authorization
* Dependency Injection
* Logging
* Configuration

ASP.NET Core begins working **after** the Web Server hands the request to it.

---

# 🧠 Important Notes

* A Server is a role, not a machine.
* A Web Server understands HTTP and HTTPS.
* Hosting means running an application and making it available for requests.
* IIS and Kestrel are both Web Servers.
* Kestrel was introduced with ASP.NET Core to support cross-platform development.
* ASP.NET Core is an Application Framework, not a Web Server.
* In production, IIS often works as a Reverse Proxy in front of Kestrel.

---

# ⭐ Golden Sentences

> A Server is a program, not a computer.

---

> A Web Server receives requests. It does not implement business logic.

---

> Kestrel is the Web Server.

---

> ASP.NET Core is the Application Framework.

---

> MVC is only one part of ASP.NET Core.

---

> Understanding architecture is more important than memorizing components.

---

# 🎤 Interview Questions

* What is a Server?
* What is the difference between a Server and a Web Server?
* What is Hosting?
* What is IIS?
* Why did Microsoft create Kestrel?
* What is the difference between IIS and Kestrel?
* What is a Reverse Proxy?
* Is ASP.NET Core a Web Server?
* Where does MVC fit inside ASP.NET Core?

---

# 📌 Summary

In this Sprint, I learned the basic architecture behind ASP.NET Core applications.

I now understand:

* What a Server is.
* What a Web Server does.
* The purpose of Hosting.
* Why IIS was used with ASP.NET Framework.
* Why Microsoft introduced Kestrel for ASP.NET Core.
* How IIS and Kestrel can work together using a Reverse Proxy.
* Why ASP.NET Core is an Application Framework rather than a Web Server.

This foundation prepares me to deeply understand how Kestrel receives requests before the ASP.NET Core Request Pipeline begins.

---

# 🚀 Next Chapter

## Sprint 03 — Deep Dive into Kestrel

### Main Questions

* How does Kestrel actually work?
* What does "Listening" really mean?
* What is a Port?
* What is a Socket?
* What happens when I execute `dotnet run`?
* Why does Visual Studio display:

```text
Now listening on: https://localhost:5001
```

---

# ✅ Sprint Result

* [x] Understand Server
* [x] Understand Web Server
* [x] Understand Hosting
* [x] Understand IIS
* [x] Understand Kestrel (Overview)
* [x] Understand Reverse Proxy
* [x] Understand ASP.NET Core Framework
* [x] Build the architectural foundation for the Request Lifecycle

**Sprint Status:** Completed ✅
