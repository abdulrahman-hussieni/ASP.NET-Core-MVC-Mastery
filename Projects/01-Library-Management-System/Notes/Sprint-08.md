# Sprint 08 — Building the ASP.NET Core Host

> **Project 01 — Library Management System**

---

# 🎯 Sprint Goal

Understand what happens when the first line of an ASP.NET Core application executes.

By the end of this Sprint, I should understand:

* What `WebApplication.CreateBuilder()` does.
* What `WebApplicationBuilder` is.
* Why Services are registered before the application starts.
* The difference between `Build()` and `Run()`.
* What the Host prepares before the application begins listening.

---

# 🧩 Prerequisites

Before starting this Sprint, I should already understand:

* .NET CLI
* Build vs Compile
* CLR
* JIT Compilation
* Entry Point
* Top-Level Statements
* Program.Main()

---

# 🗺 Journey Position

```text
Developer
    │
    ▼
dotnet run
    │
    ▼
.NET Runtime
    │
    ▼
CLR
    │
    ▼
Program.Main()
    │
    ▼
✅ WebApplication.CreateBuilder()
    │
    ▼
builder.Build()
    │
    ▼
app.Run()
```

---

# 📚 Concepts Covered

* WebApplicationBuilder
* ASP.NET Core Host
* Services
* Build()
* Run()

---

# ❓ The Problem

After the CLR executes the Entry Point...

The first line we usually see is:

```csharp
var builder = WebApplication.CreateBuilder(args);
```

But...

What exactly is a **Builder**?

Why doesn't ASP.NET Core immediately create the application?

---

# 💡 Deep Explanation

---

## Step 1 — Why Builder?

Imagine you're building a house.

Before anyone lives inside it, you first prepare everything:

* The foundation
* Electricity
* Water
* Rooms
* Doors

Only after everything is ready can people move in.

ASP.NET Core follows the same idea.

Before the application starts, it prepares everything it needs.

That's why it's called a **Builder**.

---

## Step 2 — What does CreateBuilder() do?

When this line executes:

```csharp
var builder = WebApplication.CreateBuilder(args);
```

ASP.NET Core prepares the application's infrastructure.

Behind the scenes, it starts preparing:

* The Host
* Configuration
* Logging
* Dependency Injection
* Kestrel configuration
* Environment information

At this stage...

Nothing is running yet.

The application is only being prepared.

---

## Step 3 — What is builder.Services?

One of the most important properties is:

```csharp
builder.Services
```

This is where we register everything the application will need later.

For example:

```csharp
builder.Services.AddControllersWithViews();
```

Notice something important:

This line **does not start MVC**.

It only tells ASP.NET Core:

> "This application will use MVC."

Think of it as creating a list of services that will be available after the application starts.

---

## Step 4 — Build()

After registering everything we need:

```csharp
var app = builder.Build();
```

The Builder finishes its work.

At this point:

* Configuration is prepared.
* Services are ready.
* The Host is built.

Now we finally have a real application.

Before `Build()`:

You have a Builder.

After `Build()`:

You have a running application object (`WebApplication`).

---

## Step 5 — Run()

The last step is:

```csharp
app.Run();
```

This is the moment the application actually starts.

When `Run()` executes:

* The Host starts.
* Kestrel starts.
* Ports are opened.
* The application begins listening for HTTP requests.

Without `Run()`...

The application is fully prepared, but it never starts.

---

# 🔬 Behind the Scenes

The startup flow now looks like this:

```text
Program.Main()
        │
        ▼
CreateBuilder()
        │
        ▼
Prepare Host
        │
        ▼
Register Services
        │
        ▼
Build()
        │
        ▼
Create WebApplication
        │
        ▼
Run()
        │
        ▼
Start Host
        │
        ▼
Start Kestrel
        │
        ▼
Listening...
```

---

# 💬 Assignment

## Question 1

Why doesn't ASP.NET Core create the application directly instead of using a Builder?

Explain using your own words.

---

## Question 2

Explain the difference between:

* `CreateBuilder()`
* `Build()`
* `Run()`

---

## Question 3

Does `AddControllersWithViews()` start MVC?

If not...

What does it actually do?

---

## Question 4

If we remove:

```csharp
app.Run();
```

What do you expect to happen?

Why?

---

# ⚠️ Common Misconceptions

### ❌ Misconception 1

`CreateBuilder()` starts the application.

✅ Reality

It only prepares the application's infrastructure.

---

### ❌ Misconception 2

`AddControllersWithViews()` executes MVC.

✅ Reality

It only registers MVC services.

---

### ❌ Misconception 3

`Build()` starts Kestrel.

✅ Reality

`Build()` creates the application.

`Run()` starts it.

---

### ❌ Misconception 4

`Run()` creates the application.

✅ Reality

The application already exists after `Build()`.

`Run()` only starts it.

---

# ⭐ Golden Notes

> CreateBuilder() prepares the application.

---

> Build() creates the application.

---

> Run() starts the application.

---

> Services are registered before the application starts.

---

> Kestrel starts only after `Run()`.

---

# 🎤 Interview Questions

* What is `WebApplicationBuilder`?
* Why does ASP.NET Core use the Builder pattern?
* What happens inside `CreateBuilder()`?
* What is the difference between `Build()` and `Run()`?
* Does `AddControllersWithViews()` execute MVC?
* What happens if `app.Run()` is removed?

---

# 📌 Summary

In this Sprint, I learned how ASP.NET Core prepares an application before it starts handling requests.

`CreateBuilder()` prepares the application's infrastructure.

`builder.Services` registers all required services.

`Build()` creates the final application.

Finally, `Run()` starts the Host and Kestrel, allowing the application to begin accepting HTTP requests.

---

# 🏁 Sprint Result

* [x] Understand `CreateBuilder()`
* [x] Understand `WebApplicationBuilder`
* [x] Understand Service Registration
* [x] Understand `Build()`
* [x] Understand `Run()`
* [x] Understand the Host startup sequence

**Sprint Status:** Completed ✅

---

# 🚀 Next Sprint

## Sprint 09 — Dependency Injection Fundamentals

### Main Questions

* What is Dependency Injection?
* Why do we need it?
* What problem does it solve?
* What is a Service?
* What is the Service Container?
* Why does ASP.NET Core rely heavily on DI?
