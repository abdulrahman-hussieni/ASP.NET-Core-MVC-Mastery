# Sprint 00 — Before Writing Any Code

> Project 01 — Library Management System

---

# 🎯 Sprint Goal

Understand why ASP.NET Core MVC exists before writing any code.

The objective of this Sprint is to understand the problem that MVC was designed to solve.

No coding.

No Visual Studio.

Only understanding.

---

# 📚 Concepts Covered

* Why MVC Exists
* Tight Coupling
* Separation of Concerns (SoC)
* Thinking Like a Software Engineer

---

# ❓ The Problem

Imagine building a website where everything exists inside one file:

* HTML
* CSS
* JavaScript
* C#
* SQL Queries
* Validation
* Business Logic

As the project grows, the file becomes extremely difficult to understand, modify, test, and maintain.

This was one of the biggest problems in early web development.

---

# 💡 Key Idea

The problem was **not** that developers couldn't write code.

The problem was that everything depended on everything else.

This is called:

> **Tight Coupling**

A small modification in one place could unexpectedly break another part of the application.

---

# ✅ Solution

Software engineers introduced a design principle called:

## Separation of Concerns (SoC)

Instead of placing everything in one place,

each part of the application should have a single responsibility.

Examples:

* UI
* Business Logic
* Data Access
* Validation
* Authentication

Each one belongs in its own place.

MVC is one way of applying this principle.

---

# 🧠 Important Note

MVC is **not the goal**.

MVC is simply a design pattern that helps organize an application by separating responsibilities.

The real goal is writing software that is:

* Easier to maintain
* Easier to extend
* Easier to understand
* Easier to test

---

# 💬 My Answers

## Question 1

### What problems happen if everything is placed in one file?

My answer:

* Everything becomes dependent on everything else.
* Changing one part may unexpectedly break another.
* Finding where to modify code becomes difficult.
* Adding new features becomes harder as the project grows.

---

## Question 2

### Why do companies separate responsibilities?

My answer:

Separating responsibilities makes every part of the application easier to locate, understand, modify, and extend without affecting unrelated parts of the system.

---

## Question 3

### If I were designing a framework, what would I improve?

My answer:

MVC is excellent for learning and for many real-world applications.

However, as applications become larger, responsibilities need to be separated even further.

Examples:

* Services
* Repositories
* DTOs
* Components
* Additional layers

The larger the project becomes, the more separation is needed.

---

# 📝 Mentor Feedback

### Strengths

* Good logical thinking.
* Thinking beyond syntax.
* Started connecting project size with architecture.

---

### Things to Improve

Instead of thinking only about organizing files,

always think about solving software complexity.

The objective of architecture is not beautiful folders.

The objective is making software easier to maintain, scale, test, and develop.

---

# ⭐ Golden Sentence

> Software Engineering is not about writing code.

> It is about managing complexity.

---

# 🎤 Interview Question

**Why do we use MVC?**

Current understanding:

MVC is not used simply to separate files.

It is used to help organize responsibilities, reduce coupling, improve maintainability, and make software easier to extend as it grows.

---

# 🚀 Sprint Result

* [x] Understand the problem.
* [x] Understand Tight Coupling.
* [x] Understand Separation of Concerns.
* [x] Complete first discussion.
* [x] Pass first review.

Sprint Status:

**Completed ✅**
