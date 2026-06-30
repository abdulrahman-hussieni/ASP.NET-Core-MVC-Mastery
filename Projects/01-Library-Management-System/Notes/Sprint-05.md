# Sprint 05 — The .NET Execution Pipeline

> **Project 01 — Library Management System**

---

# 🎯 Sprint Goal

Understand what actually happens when executing an ASP.NET Core application.

By the end of this Sprint, I should understand:

* What `.NET CLI` is.
* The difference between Build and Compile.
* What Intermediate Language (IL) is.
* What the .NET Runtime is.
* What the CLR is responsible for.
* The startup sequence before ASP.NET Core begins running.

---

# 🧩 Prerequisites

Before starting this Sprint, I should already understand:

* HTTP Fundamentals
* Server & Web Server
* Hosting
* IIS
* Kestrel
* ASP.NET Core Host
* Program vs Process
* Port
* Socket

---

# 🗺 Request Journey Overview

```text
Developer
    │
    ▼
dotnet run
    │
    ▼
.NET CLI
    │
    ▼
MSBuild
    │
    ▼
Compile
    │
    ▼
Generate IL
    │
    ▼
.NET Runtime
    │
    ▼
CLR
    │
    ▼
Create Process
    │
    ▼
ASP.NET Core Host
    │
    ▼
Kestrel
    │
    ▼
Listening
    │
    ▼
HTTP Request Starts
```

---

## 📍 Current Position

```text
Developer
    ↓
✅ dotnet run
    ↓
.NET CLI
    ↓
MSBuild
    ↓
Compile
    ↓
IL
```

This Sprint focuses on everything that happens **before** the application starts listening for HTTP requests.

---

# 📚 Concepts Covered

* .NET CLI
* MSBuild
* Build
* Compile
* Intermediate Language (IL)
* .NET Runtime
* CLR

---

# ❓ The Problem

Every ASP.NET Core developer executes:

```bash
dotnet run
```

But...

What actually happens?

Does ASP.NET Core start immediately?

Does Kestrel start first?

Who builds the project?

Who executes the application?

---

# 💡 Key Concepts

---

## 1. .NET CLI

The **.NET CLI (Command Line Interface)** is the command-line tool used by developers to interact with the .NET ecosystem.

Examples:

```bash
dotnet new mvc
dotnet restore
dotnet build
dotnet run
dotnet publish
```

The CLI is responsible for orchestrating different tools such as:

* MSBuild
* NuGet
* .NET Runtime

It is **not** the Runtime.

It is **not** ASP.NET Core.

It is simply the tool used to execute commands.

---

## 2. Build vs Compile

Many developers think these two words have the same meaning.

They do not.

### Compile

Compile is the process of translating C# source code into Intermediate Language (IL).

```text
C#
    ↓
Compiler
    ↓
IL
```

### Build

Build is a larger workflow.

It includes:

* Restore NuGet Packages
* Compile source code
* Generate assemblies (.dll)
* Prepare output files

```text
Build
│
├── Restore Packages
├── Compile
├── Generate Assemblies
└── Prepare Output
```

Compile is only one step inside Build.

---

## 3. Intermediate Language (IL)

C# is **not** compiled directly into Machine Code.

Instead:

```text
C#
    ↓
Compiler
    ↓
Intermediate Language (IL)
```

Why?

Because IL is platform-independent.

The same IL can later run on:

* Windows
* Linux
* macOS

without recompiling the source code.

---

## 4. .NET Runtime

The Runtime is the execution environment where .NET applications run.

It provides:

* Core Libraries
* Memory Management
* Thread Management
* Garbage Collection
* CLR

Without the Runtime, a normal framework-dependent .NET application cannot execute.

---

## 5. CLR (Common Language Runtime)

The CLR is the execution engine of .NET.

Responsibilities include:

* Executing IL Code
* Just-In-Time (JIT) Compilation
* Garbage Collection
* Exception Handling
* Thread Management
* Assembly Loading
* Type Safety
* Security Verification

A useful mental model:

> The CLR is the execution engine that manages everything while your .NET application is running.

---

# 🚀 Startup Sequence

```text
Developer
      │
      ▼
dotnet run
      │
      ▼
.NET CLI
      │
      ▼
Read .csproj
      │
      ▼
Restore Packages
      │
      ▼
MSBuild
      │
      ▼
Compile
      │
      ▼
Generate IL (.dll)
      │
      ▼
.NET Runtime
      │
      ▼
CLR
      │
      ▼
Create Process
      │
      ▼
ASP.NET Core Host
      │
      ▼
Start Kestrel
      │
      ▼
Now Listening...
```

---

# 💬 My Answers

---

## Question 1

### Explain the difference between .NET CLI, Runtime and CLR.

### My Answer

**.NET CLI**

The command-line tool used by developers to create, build, run and publish .NET applications.

It orchestrates the tools required to execute those operations.

---

**.NET Runtime**

The execution environment required to run .NET applications.

It contains the runtime libraries and hosts the CLR.

---

**CLR**

The execution engine inside the Runtime.

It executes IL, performs JIT compilation, manages memory, handles exceptions, controls threads and provides runtime services.

---

### Mentor Feedback

Excellent explanation.

Small improvement:

The Runtime is not just a collection of files.

Think of it as the complete execution environment where managed applications live.

---

## Question 2

### Why is Build different from Compile?

### My Answer

Compile is only one step.

It translates C# into IL.

Build is the complete workflow.

It restores packages, compiles source code, generates assemblies and prepares the application output.

---

### Mentor Feedback

Excellent.

Remember:

```text
Compile ⊂ Build
```

Compile is part of Build.

---

## Question 3

### Why does .NET compile to IL instead of Machine Code directly?

### My Answer

Because IL provides platform independence.

The same application can run on different operating systems without recompiling.

It also allows multiple .NET languages such as C#, F# and VB.NET to target the same execution environment.

---

### Mentor Feedback

Excellent.

Another important reason is that IL enables runtime services provided by the CLR, including Reflection, Metadata inspection and Dynamic Loading.

---

## Question 4

### Why does the CLR exist?

### My Answer

Without the CLR, developers would lose automatic memory management, runtime safety and many advanced runtime services.

The CLR provides:

* Garbage Collection
* Security
* Type Safety
* JIT Compilation
* Exception Handling
* Thread Management

---

🛑 السؤال الأول: الفرق بين .NET CLI و .NET Runtime و CLR
عشان ما تتلخبطش بينهم تاني خالص، تخيل إننا بنبني "عمارة":

1. الـ .NET CLI (واجهة الأوامر - Command Line Interface)
هو: "الـ عِدّة والمطارق والأدوات بتاعة البنا".

شغلته: ده البرنامج اللي بتكتبله أوامر في الـ Terminal زي dotnet new أو dotnet build أو dotnet run. هو الأداة اللي في إيدك كمطور عشان تكريت المشروع وتعمله بناء.

2. الـ .NET Runtime (بيئة التشغيل)
هو: "موقع السقالات والخدمات المحيطة بالعمارة عشان العمال يعرفوا يشتغلوا".

شغلته: ده البايدج (Package) الكبيرة اللي لازم تنزل على جهاز العميل عشان برنامج الـ .NET يشتغل أصلاً. جواه كل المكتبات الجاهزة (Libraries) والـ Garbage Collector وكمان جواه الـ CLR. من غيره، الجهاز مش هيعرف يعني إيه تطبيق .NET.

3. الـ CLR (الـ Common Language Runtime)
هو: "المهندس الاستشاري المقيم جوة الموقع اللي بيشرف على العمال لحظة بلحظة".

شغلته: ده الموتور أو "القلب النابض" جوة الـ Runtime. هو اللي بياخد الكود ويترجمه للغة الآلة (Machine Code) أثناء التشغيل، وهو اللي بيراقب الذاكرة ويشيل الزبالة منها (Garbage Collection)، وبيضمن إن الكود أمان وما يعملش كراش للسيرفر.

🛑 السؤال الثاني: ليه Build مش هو الـ Compile؟
كتير بيفكروهم نفس الحاجة، بس في الحقيقة: الـ Compile هو جزء صغير من عملية الـ Build الكاملة.

الـ Compile (الترجمة): هو مجرد مترجم لغوي. بياخد ملفات الكود اللي أنت كاتبها بالـ C# ويترجمها لملفات لغة وسيطة (IL Code). خطوة واحدة وبس.

الـ Build (البناء المتكامل): دي العملية الكبيرة (الـ Workflow كاملاً). لما تعمل Build، الـ CLI بيعمل كذا حاجة بالترتيب:

بيعمل Restore ويحمل كل المكتبات الخارجية (NuGet Packages) اللي المشروع محتاجها.

بيعمل Compile للكود بتاعك ويحوله لـ IL.

بيجمع الصور، ملفات الإعدادات (appsettings.json)، والـ Assets التانية.

بيحط كل ده في فولدر الـ bin ويطلعلك المنتج النهائي (ملف الـ .dll أو الـ .exe) الجاهز للتشغيل.

🛑 السؤال الثالث: ليه Microsoft بتحول C# ← IL ← Machine Code بدل ما تحول لـ Machine Code على طول؟
لو مايكروسوفت خلت الـ C# تترجم لـ Machine Code علطول، كنا هنقع في مشكلتين كبار جداً:

1. مرونة أنظمة التشغيل والـ Hardware (Cross-Platform)
الـ Machine Code بتاع معالج Intel على Windows، يختلف تماماً عن معالج M3 على Mac، يختلف عن معالج ARM على سيرفر Linux.
لو بنحول لـ Machine Code علطول، كان المطور هيضطر يعمل Compile بنسخة مخصوصة لكل جهاز في العالم!
لكن الـ IL (Intermediate Language) هي لغة موحدة ومحايدة. الـ C# بيتحول لـ IL مرة واحدة بس، والـ IL ده يروح لأي جهاز في الدنيا، وهناك الـ CLR بتاع الجهاز ده يترجمه للـ Machine Code اللي بيفهمه المعالج بتاعه بالظبط (عبر حاجة اسمها الـ JIT Compiler).

2. تعدد اللغات (Language Interoperability)
تخيل إن مايكروسوفت عندها لغات تانية زي F# و VB.NET. بفضل الـ IL، كل اللغات دي بتتترجم لنفس اللغة الوسيطة في الآخر. ده معناه إنك تقدر تكتب كود بـ C# وتستخدمه جوة مشروع مكتوب بـ F# من غير أي مشاكل لأنهم في النهاية بيتكلموا نفس الـ IL!

🛑 السؤال الرابع: في رأيك ليه CLR موجود؟ ليه منخليش البرنامج يتحول Machine Code وخلاص؟
لو شيلنا الـ CLR وخلينا البرنامج يتحول لـ Machine Code علطول (زي لغة C++ مثلاً)، هنكسب سرعة أعلى بحاجة بسيطة، بس هنخسر مميزات تانية خرافية بتخلي الـ .NET قوي وآمن:

إدارة الذاكرة التلقائية (Garbage Collection): في اللغات اللي بتتحول لـ Machine Code علطول، المطور هو اللي لازم يحجز مكان في الذاكرة ويمسحه بنفسه. لو نسي، السيرفر هيحصله Memory Leak ويقع. الـ CLR بيشيل القرف ده عنك ويدير الذاكرة أوتوماتيك.

الأمان والحماية (Type Safety & Sandboxing): الـ CLR بيشتغل كـ "حارس بوابة". قبل ما يشغل أي كود، بيتأكد إن الكود ده مش هيضرب الذاكرة، ومش هيحاول يوصل لأماكن ممنوعة في نظام التشغيل، وده بيمنع ثغرات أمنية كارثية.

الـ Just-In-Time (JIT) Optimization: الـ CLR مش بس بيترجم لـ Machine Code، ده وهو بيترجم على جهاز العميل، بيشوف نوع المعالج إيه بالظبط ويطلع Machine Code "متفصل ومتحسن" خصيصاً لنوع المعالج ده عشان يديك أعلى كفاءة ممكنة لحظتها.

🧠 جملة ذهبية تقفل بيها السبرينت ده:

الـ IL والـ CLR هما السر اللي بيخلوا الـ .NET يشتغل "في أي مكان، بأعلى أمان، ومن غير ما المطور يشيل هم إدارة الذاكرة".
---
### Mentor Feedback

Excellent.

One clarification:

The CLR does not exist only for JIT.

It is the complete execution engine responsible for running managed applications.

---

# ⚠️ Common Misconceptions

### ❌ Build = Compile

✅ Reality:

Compile is only one phase of Build.

---

### ❌ dotnet = Runtime

✅ Reality:

`dotnet` is the CLI.

---

### ❌ CLR = Runtime

✅ Reality:

The CLR is one component inside the Runtime.

---

### ❌ C# compiles directly into Machine Code

✅ Reality:

C# compiles into IL.

The CLR later transforms IL into Machine Code using JIT.

---

# 🧠 Important Notes

* `dotnet` is the CLI.
* Build includes Compile.
* C# compiles to IL.
* IL is platform-independent.
* The Runtime hosts the CLR.
* The CLR executes managed code.
* ASP.NET Core has not started yet during most of these steps.

---

# ⭐ Golden Sentences

> Build is a workflow. Compile is one step inside that workflow.

---

> The .NET CLI executes commands. It does not execute your application.

---

> C# is compiled into IL, not directly into Machine Code.

---

> The Runtime provides the environment. The CLR provides the execution engine.

---

> Managed applications run inside the CLR.

---

# 🎤 Interview Questions

* What is the .NET CLI?
* What happens when you execute `dotnet run`?
* What is the difference between Build and Compile?
* What is IL?
* What is the .NET Runtime?
* What is the CLR?
* Why doesn't C# compile directly into Machine Code?
* Why does .NET use IL?

---

# 📌 Summary

In this Sprint, I learned what happens before an ASP.NET Core application actually starts.

I now understand the complete execution pipeline from `dotnet run` until the CLR begins executing the application.

I also understand the responsibilities of the .NET CLI, MSBuild, Build, Compile, IL, Runtime and CLR.

This Sprint forms the foundation for understanding how the ASP.NET Core Host starts and eventually launches Kestrel.

---

# 🚀 Next Sprint

## Sprint 06 — The Complete Startup Sequence

### Main Questions

* What happens after the CLR starts executing the application?
* Where does `Program.cs` fit into the startup sequence?
* Who creates the Host?
* When is `WebApplication.CreateBuilder()` executed?
* When does Kestrel actually start listening?
* Why is `Program.cs` not the first code that executes?

---

# ✅ Sprint Result

* [x] Understand .NET CLI
* [x] Understand MSBuild
* [x] Understand Build vs Compile
* [x] Understand Intermediate Language (IL)
* [x] Understand .NET Runtime
* [x] Understand CLR
* [x] Understand the execution pipeline before ASP.NET Core starts
* [x] Complete Assignment
* [x] Pass Mentor Review

**Sprint Status:** Completed ✅
