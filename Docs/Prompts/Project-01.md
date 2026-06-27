# Project 01 — Library Management System

> **Project 01 — Beginner Level**

---

# 🎯 Goal

Build a simple Library Management System to master the fundamentals of **ASP.NET Core MVC**.

This project intentionally keeps the business logic simple so the focus remains on understanding how ASP.NET Core MVC works internally and how to build clean, maintainable applications.

---

# 📚 What Will I Learn

During this project I will learn:

* MVC Fundamentals
* ASP.NET Core Project Structure
* Entity Framework Core
* CRUD Operations
* Data Validation
* Data Access Layer
* Dependency Injection
* Data Presentation
* File Management
* Error Handling
* Logging

---

# 🧠 Key Concepts

## MVC Fundamentals

* MVC Architecture
* Request Lifecycle
* Routing
* Controllers
* Actions
* Views
* Razor Syntax
* Layouts
* Partial Views
* View Components
* Models
* ViewModels
* ViewData
* ViewBag
* TempData

---

## Entity Framework Core

* DbContext
* SQL Server Connection
* Migrations
* LINQ
* Relationships
* CRUD Operations

---

## Data Validation

* Data Annotations
* Model Validation
* Custom Validation (Introduction)

---

## Data Access Layer

* Repository Pattern (Basic)

---

## Dependency Injection

* Built-in Dependency Injection
* Service Registration

---

## Data Presentation

* Search
* Sorting
* Filtering
* Pagination

---

## File Management

* Image Upload
* Static Files

---

## Error Handling

* Exception Handling
* Custom Error Pages

---

## Logging

* Built-in Logging

---

# 🗄 Database Overview

The database is intentionally small.

It contains only three tables.

### Authors

Stores book authors.

---

### Categories

Stores book categories.

---

### Books

Stores book information.

Each book belongs to:

* One Author
* One Category

Relationship:

```
Author (1) ------ (*) Books (*) ------ (1) Category
```

---

# 📋 Features

* Manage Authors
* Manage Categories
* Manage Books
* Upload Book Images
* Search Books
* Sort Books
* Filter Books
* Pagination
* Input Validation
* Responsive UI

---

# 📈 Progress

## Sprint 0

* [ ] Understanding MVC
* [ ] Understanding Project Architecture
* [ ] Database Design

---

## Sprint 1

* [ ] Create Project
* [ ] Configure SQL Server
* [ ] Configure Entity Framework Core

---

## Sprint 2

* [ ] Create Models
* [ ] Configure Relationships
* [ ] Create Migrations

---

## Sprint 3

* [ ] Authors CRUD

---

## Sprint 4

* [ ] Categories CRUD

---

## Sprint 5

* [ ] Books CRUD

---

## Sprint 6

* [ ] Validation

---

## Sprint 7

* [ ] Search & Filtering

---

## Sprint 8

* [ ] Pagination & Sorting

---

## Sprint 9

* [ ] Image Upload

---

## Sprint 10

* [ ] Refactoring
* [ ] Final Review

---

# 🤖 AI Prompt

This project is taught by following one simple principle:

> **Understand First. Code Second.**

The AI acts as a senior ASP.NET Core mentor.

Rules:

* Explain every concept before implementation.
* Explain why each concept exists.
* Build one feature at a time.
* Never generate the whole project.
* Review the code after every Sprint.
* Ask interview questions.
* Give small practical challenges.
* Suggest better approaches when appropriate.

The goal is not to finish quickly.

The goal is to deeply understand ASP.NET Core MVC and build a strong foundation for the next projects.
