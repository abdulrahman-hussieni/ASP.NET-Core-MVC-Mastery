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

---
# Lesson 03 — Inside the Browser
---


## Browser Responsibilities

The Browser performs the following steps before sending the Request:

```text
                                                User presses Enter
                                                        │
                                                        ▼
                                                Read URL
                                                        │
                                                        ▼
                                                Parse URL
                                                        │
                                                        ▼
                                                Check Browser Cache
                                                        │
                                                        ▼
                                                DNS Lookup
                                                        │
                                                        ▼
                                                Open TCP Connection
                                                        │
                                                        ▼
                                                TLS Handshake (HTTPS)
                                                        │
                                                        ▼
                                                Create HTTP Request
                                                        │
                                                        ▼
                                                Send HTTP Request
```

---

### Step 1 — Read URL
    The Browser reads the URL entered by the user.
    Example:
            https://localhost:5001/books

At this point, nothing has been sent to the Server.

---

### Step 2 — Parse URL

The Browser separates the URL into:
        - Protocol
        - Host
        - Port
        - Path
        - Query String
        
---

### Step 3 — Browser Cache

Before contacting the Server, the Browser checks whether the required resources already exist in its local Cache.

#### Cached resources may include:

        - Images
        - CSS
        - JavaScript
        - Fonts

If a valid cached version exists, the Browser may reuse it instead of requesting it again.

---

### Step 4 — DNS Lookup
        If the Host is a Domain Name, the Browser must obtain its IP Address.
Example:

```text
google.com
        │
        ▼
142.x.x.x
```

For localhost:

```text
localhost
        │
        ▼
127.0.0.1
```

---

### Step 5 — Open TCP Connection

    - After obtaining the IP Address, the Browser opens a TCP Connection with the Server.
    - This connection allows data to travel between the Client and the Server.

---

### Step 6 — TLS Handshake

If HTTPS is used, the Browser performs a TLS Handshake before sending any data.
        The purpose is:
        
        - Encrypt the communication.
        - Verify the Server identity.
        - Establish a secure connection.

---

### Step 7 — Create HTTP Request

After the connection is ready, the Browser builds the HTTP Request according to the HTTP Protocol.

---

### Step 8 — Send HTTP Request

Finally, the Browser sends the HTTP Request.

```text
                                                Browser
                                                        │
                                                        ▼
                                                HTTP Request
                                                        │
                                                        ▼
                                                Kestrel
```

At this point the Request leaves the Client.

---

### After Receiving the Response

The Browser continues working.

It:

    - Reads the Response.
    - Parses HTML.
    - Downloads CSS.
    - Downloads JavaScript.
    - Downloads Images.
    - Builds the DOM.
    - Renders the final page.

A Browser does much more than simply displaying HTML.

---
# Lesson 04 — HTTP Protocol & HTTP Request
---

## 🎯 Goal

Understand what HTTP is, why it exists, and how an HTTP Request is structured.

---

## 📍 Current Position

```text
               User
                │
                ▼
              Browser
                │
                ▼
            HTTP Request
```

---

## Why Do We Need HTTP?

Without a common protocol:

- Every Browser would communicate differently.
- Every Server would expect different message formats.
- The Web would not work.

HTTP standardizes communication for everyone.

---

## HTTP Messages

HTTP defines two message types:

```text
                HTTP Request
                
                    ↓
                
                HTTP Response
```

The Client sends a Request.

The Server returns a Response.

---

## HTTP Request Structure

Every HTTP Request contains three main parts:

```text
            HTTP Request
            
            │
            
            ├── Request Line
            
            ├── Headers
            
            └── Body (Optional)
```

---

### Request Line
    The first line of every HTTP Request.

    GET /books?page=2 HTTP/1.1

    It consists of:

    - HTTP Method
    - Request Target (Path)
    - HTTP Version

---

### HTTP Method

Defines the intended operation.

    - GET
    - POST
    - PUT
    - PATCH
    - DELETE

---

### Request Target

Represents the requested Resource.

Examples:
```text
            /books
            
            /books/15
            
            /api/products
```
---

### HTTP Version
    Specifies which version of HTTP is being used.
Examples:

    - HTTP/1.1
    - HTTP/2
    - HTTP/3

---

### Headers
    Headers contain metadata about the Request.
Examples:
```http
    Host: localhost:5001
    
    Accept: text/html
    
    User-Agent: Chrome
```

    Headers describe the Request but do not contain the actual business data.

---

### Body
    The Body contains the actual data being sent to the Server.

Usually appears with:

- POST
- PUT
- PATCH

Example:

```json
        {
            "title":"Clean Code",
            "price":100
        }
```

GET Requests usually do not contain a Body.

---

## Complete HTTP Request Example

```http
        POST /books HTTP/1.1
        
        Host: localhost:5001
        
        Content-Type: application/json
        
        Accept: application/json
        
        {
            "title":"Clean Code",
            "price":100
        }
```

---
# Lesson 07 — HTTP Body

## 💡 Concepts

    The HTTP Body contains the actual data sent from the Client to the Server.
    Unlike Headers, which describe the Request, the Body contains the business data itself.

Examples include:

    - User registration data
    - Login credentials
    - Product information
    - Uploaded files
    - JSON objects

---

## Does Every Request Have a Body?    No.

The Body is optional.

Generally:

| Method | Body |
|---------|------|
| GET | Usually No |
| POST | Usually Yes |
| PUT | Usually Yes |
| PATCH | Usually Yes |
| DELETE | Optional |

---

## Why Doesn't GET Usually Have a Body?

    GET requests are designed to retrieve data.
    The requested resource is already identified by:
        - URL
        - Path
        - Query String
---

## POST Request Example

```http
POST /books HTTP/1.1

Content-Type: application/json

{
    "title":"Clean Code",
    "price":100
}
```

Everything inside the JSON object belongs to the Request Body.

---

## Common Body Formats

### JSON

The most common format in modern APIs.

Example:

```json
{
    "title":"Clean Code",
    "price":100
}
```

---

### Form URL Encoded

Commonly generated by HTML Forms.

Example:

```text
Title=Clean Code&Price=100
```

---

### Multipart Form Data

Used when uploading files.

Example:

- Image
- PDF
- Document

---

## Headers vs Body

| Headers | Body |
|----------|------|
| Metadata | Actual Data |
| Small | Can be very large |
| Usually Always Present | Optional |

---

## 🧪 Mini Lab

Using Postman:

Create a POST Request.

Send:

```json
{
    "title":"Clean Code",
    "price":100
}
```

Observe:

- Request Body
- Content-Type
- Response

Then change the Body type to Form Data and compare the Request.

---
# Lesson 08 — HTTP Response
---

## 💡 Concepts

        After processing the Request, the Server returns an HTTP Response.
        
        The Response tells the Client:
        
        - Whether the Request succeeded.
        - What data should be returned.
        - How that data should be interpreted.

---

## HTTP Response Structure

Every HTTP Response consists of:

```text
        HTTP Response
        
        │
        
        ├── Status Line
        
        ├── Headers
        
        └── Body
```

---

## Status Line : The first line of every Response.

Example:

```http
HTTP/1.1 200 OK
```
    It contains:
    - HTTP Version
    - Status Code
    - Status Message

---

## Response Headers

Examples:
```http
        Content-Type: text/html
        
        Content-Length: 1024
        
        Cache-Control: no-cache
        
        Set-Cookie: ...
        
        Location: /Home
```
---

## Response Body

The Body contains the actual data returned by the Server.

It may contain:
        - HTML
        - JSON
        - Images
        - CSS
        - JavaScript
        - PDF
        - Video
        - Any binary file

The Body is **not limited to HTML**.

---

## Request vs Response

| Request | Response |
|---------|----------|
| Sent by Client | Sent by Server |
| Contains Request information | Contains Result |
| Starts with Method | Starts with Status Line |

---

## Browser Processing

After receiving the Response, the Browser performs the following steps:

```text
            Receive Response
                ↓
            Read Status Code
                ↓
            Read Headers
                ↓
            Read Body
                ↓
            Render Content
```


## 🧪 Mini Lab

Open Chrome DevTools.

Go to:

Network

Select any Request.

Inspect:

- Status Code
- Response Headers
- Response Body

Compare:

- HTML page
- CSS file
- JavaScript file
- Image
- API Response

Observe how each Response changes while following the same HTTP structure.

---
# Lesson 09 — HTTP Status Codes
---

## 💡 Concepts
    Every HTTP Response starts with a **Status Line**.

```http
    HTTP/1.1 200 OK
```

    The Status Code tells the Client whether the Request succeeded, failed, or requires another action.
    Without Status Codes, the Browser would not know whether the Request completed successfully.

---

## Status Code Categories

| Category | Meaning |
|----------|---------|
| 1xx | Informational |
| 2xx | Success |
| 3xx | Redirection |
| 4xx | Client Errors |
| 5xx | Server Errors |

---
## 1xx — Informational
        Temporary informational responses.
        Rarely encountered in everyday ASP.NET Core development.

---
## 2xx — Success : The Request completed successfully.

| Code | Description |
|------|-------------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |

---
### 200 OK
        The Request succeeded.
        Usually returned after successful GET Requests.
---
### 201 Created
        Returned after creating a new Resource.
        Common with POST Requests.
---
### 204 No Content
        The operation succeeded but there is no Response Body.
        Common after DELETE operations.
---
---
## 3xx — Redirection
    The requested Resource is available somewhere else.
Common examples:

| Code | Description |
|------|-------------|
| 301 | Permanent Redirect |
| 302 | Temporary Redirect |

Browsers automatically follow Redirect Responses.

---
## 4xx — Client Errors
    The Request contains a problem.
    The Server is working correctly.

Examples:
| Code | Description |
|------|-------------|
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
---
### 400 Bad Request
    The Request format is invalid.
---
### 401 Unauthorized
    Authentication is required.
    The Client has not logged in.
---
### 403 Forbidden
    Authentication succeeded.
    However, the Client is not allowed to access the requested Resource.
---
### 404 Not Found
    The requested Resource does not exist.
---
---
## 5xx — Server Errors
    The Request reached the Server successfully.
    However, the Server failed while processing it.
Examples:
| Code | Description |
|------|-------------|
| 500 | Internal Server Error |
| 503 | Service Unavailable |
---
### 500 Internal Server Error
    Unexpected Server-side exception.
---
### 503 Service Unavailable
    The Server is temporarily unavailable.
    Examples:
    
    - Maintenance
    - Overloaded Server
---

## 401 vs 403

| 401 | 403 |
|------|------|
| Authentication required | Authentication succeeded |
| User identity unknown | User identity known |
| Login required | Permission denied |

---

## 404 vs 500

| 404 | 500 |
|------|------|
| Resource not found | Server crashed while processing |
| Client requested invalid resource | Server has an internal problem |

---

---
# Lesson 10 — Practical Lab (Chrome DevTools & Postman)
---

## What Should You Inspect?

### General Information
    - Request URL
    - Request Method
    - Status Code
    - Remote Address

---

### Request Headers

Find:
    - Host
    - User-Agent
    - Accept
    - Accept-Language
    - Content-Type
    - Cookie

---

### Response Headers

Find:

- Content-Type
- Content-Length
- Cache-Control
- Set-Cookie
- Location

---

### Request Body
    If the Request is POST or PUT, inspect the transmitted data.
---

### Response Body
    Compare different Response types:
        - HTML
        - JSON
        - CSS
        - JavaScript
        - Images
---

### Timing
    Observe:
        - DNS
        - Connection
        - SSL
        - Waiting
        - Download
---
