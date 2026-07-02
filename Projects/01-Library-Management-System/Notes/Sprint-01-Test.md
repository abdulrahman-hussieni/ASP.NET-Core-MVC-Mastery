# Sprint 01 — Knowledge Check

> **Project:** Library Management System
>
> This Knowledge Check reviews everything covered in Sprint 01.
>
> Try answering each question before reading the answer.

---

# Part 01 — HTTP Fundamentals

---

## Question 01

### What is a Protocol?

### ✅ Answer

A Protocol is a set of communication rules that defines how two systems exchange data.

Examples include:

- HTTP
- HTTPS
- FTP
- SMTP

Without protocols, different systems would not understand each other.

---

## Question 02

### Why do we need Protocols?

### ✅ Answer

Protocols standardize communication between Clients and Servers.

Without protocols:

- Every Browser would communicate differently.
- Every Server would expect different message formats.
- The Internet would not work consistently.

---

## Question 03

### What is HTTP?

### ✅ Answer

HTTP (HyperText Transfer Protocol) is an application-layer communication protocol used by Clients and Servers to exchange Requests and Responses.

HTTP defines:

- Request format
- Response format
- Methods
- Headers
- Status Codes

---

## Question 04

### Is HTTP responsible for security?

### ✅ Answer

No.

HTTP only defines communication rules.

Secure communication is provided by HTTPS using TLS encryption.

---

## Question 05

### What is HTTPS?

### ✅ Answer

HTTPS is HTTP secured with TLS.

It encrypts data exchanged between the Client and the Server.

HTTPS provides:

- Confidentiality
- Integrity
- Authentication

---

## Question 06

### What is the difference between HTTP and HTTPS?

### ✅ Answer

HTTP transfers data without encryption.

HTTPS encrypts communication using TLS, protecting the transmitted data.

---

## Question 07

### What is a Client?

### ✅ Answer

A Client is any application that sends HTTP Requests.

Examples:

- Browser
- Postman
- Mobile Application
- Desktop Application

---

## Question 08

### What is a Server?

### ✅ Answer

A Server is an application that receives Requests, processes them, and returns Responses.

---

## Question 09

### What is an HTTP Request?

### ✅ Answer

An HTTP Request is a message sent by the Client to the Server asking it to perform an operation.

---

## Question 10

### What is an HTTP Response?

### ✅ Answer

An HTTP Response is the message returned by the Server after processing the Request.

It contains:

- Status Line
- Headers
- Body

---

# Part 02 — URL Fundamentals

---

## Question 11

### What is a URL?

### ✅ Answer

A URL (Uniform Resource Locator) identifies the location of a resource on the Web and specifies how to access it.

---

## Question 12

### What are the parts of a URL?

### ✅ Answer

A URL consists of:

- Protocol
- Host
- Port
- Path
- Query String

---

## Question 13

### Explain this URL.

```text
https://localhost:5001/books/15?page=2
```

### ✅ Answer

Protocol

```
https
```

Host

```
localhost
```

Port

```
5001
```

Path

```
/books/15
```

Query String

```
?page=2
```

---

## Question 14

### What is the Protocol part of the URL?

### ✅ Answer

The Protocol defines the communication rules used between the Client and the Server.

Examples:

- HTTP
- HTTPS

---

## Question 15

### What is the Host?

### ✅ Answer

The Host identifies the destination machine that should receive the Request.

Examples:

- localhost
- google.com
- github.com

---

## Question 16

### What is an IP Address?

### ✅ Answer

An IP Address uniquely identifies a device on a network.

Example:

```
192.168.1.10
```

---

## Question 17

### Why do we use Domain Names instead of IP Addresses?

### ✅ Answer

Because Domain Names are easier for humans to remember than numeric IP Addresses.

DNS translates Domain Names into IP Addresses.

---

## Question 18

### What is localhost?

### ✅ Answer

localhost always refers to the current machine.

It resolves to:

```
127.0.0.1
```

---

## Question 19

### What is a Port?

### ✅ Answer

A Port identifies which application running on a machine should receive the incoming Request.

---

## Question 20

### Why do we need Ports?

### ✅ Answer

A single computer can run multiple applications simultaneously.

Examples:

- Kestrel
- SQL Server
- IIS
- Docker

Ports distinguish between these applications.

---

## Question 21

### Why are Ports 80 and 443 usually hidden?

### ✅ Answer

Because they are the default Ports.

HTTP defaults to Port 80.

HTTPS defaults to Port 443.

Browsers automatically omit default Ports from the URL.

---

## Question 22

### What is the Path?

### ✅ Answer

The Path identifies the requested resource on the Server.

Example:

```
/books/15
```

---

## Question 23

### What is a Query String?

### ✅ Answer

The Query String contains additional parameters sent with the Request.

Example:

```
?page=2&sort=name
```

It is commonly used for:

- Filtering
- Searching
- Sorting
- Pagination

---

## Question 24

### What is the difference between Path and Route?

### ✅ Answer

The Path is part of the URL.

The Route is the ASP.NET Core configuration that matches a Path to an Endpoint.

---

## Question 25

### What is URL Encoding?

### ✅ Answer

URL Encoding converts reserved characters into a safe format that can be transmitted inside a URL.

Example:

```
Space

↓

%20
```

Example:

```
Clean Code

↓

Clean%20Code
```

---

## Question 26

### What is the difference between URL and URI?

### ✅ Answer

URI is the general identifier.

URL is a URI that also specifies the resource location.

Every URL is a URI, but not every URI is a URL.

---

## Question 27

### What is the difference between Absolute URL and Relative URL?

### ✅ Answer

Absolute URL contains the complete address.

Example:

```
https://localhost:5001/books
```

Relative URL depends on the current location.

Example:

```
/books
```

---

## Question 28

### What is FQDN?

### ✅ Answer

FQDN (Fully Qualified Domain Name) is the complete domain name including all hierarchy levels.

Example:

```
www.google.com
```

---

## Question 29

### What is a Virtual Directory?

### ✅ Answer

A Virtual Directory allows multiple applications to be hosted under the same Domain.

Example:

```
https://company.com/hr
```

---

## Question 30

### Why does the Browser need the Host before sending the Request?

### ✅ Answer

Because the Browser must know the destination machine before creating a network connection.

Without the Host, the Browser would not know where to send the Request.

---
# Part 03 — Browser Internal Work

---

## Question 31

### What happens immediately after the user presses Enter?

### ✅ Answer

The Browser starts processing the URL. It does not send the Request immediately. It first parses the URL, checks the cache, resolves the Host, establishes a connection, and finally creates the HTTP Request.

---

## Question 32

### What are the Browser's main responsibilities?

### ✅ Answer

The Browser is responsible for:

- Reading the URL
- Parsing the URL
- Checking the Browser Cache
- Resolving the Host (DNS)
- Opening a TCP Connection
- Performing the TLS Handshake (HTTPS)
- Creating the HTTP Request
- Sending the HTTP Request
- Receiving the HTTP Response
- Rendering the Response

---

## Question 33

### Does the Browser immediately contact ASP.NET Core after pressing Enter?

### ✅ Answer

No.

Several operations occur before any communication with the Server begins, such as URL parsing, cache lookup, DNS resolution, and connection establishment.

---

## Question 34

### Why does the Browser parse the URL?

### ✅ Answer

To separate the URL into its components:

- Protocol
- Host
- Port
- Path
- Query String

Each component is used while building the HTTP Request.

---

## Question 35

### Why does the Browser check its Cache first?

### ✅ Answer

To avoid downloading resources that already exist locally, improving performance and reducing network traffic.

---

## Question 36

### What is DNS?

### ✅ Answer

DNS (Domain Name System) translates Domain Names into IP Addresses.

Example:

```
google.com

↓

142.x.x.x
```

---

## Question 37

### Why is DNS required?

### ✅ Answer

Because computers communicate using IP Addresses, while humans use Domain Names.

DNS bridges the gap between them.

---

## Question 38

### What happens if the Host is localhost?

### ✅ Answer

localhost resolves to:

```
127.0.0.1
```

The Browser communicates with the local machine instead of a remote Server.

---

## Question 39

### Why is a TCP Connection required?

### ✅ Answer

TCP establishes a reliable communication channel between the Client and the Server before data is exchanged.

---

## Question 40

### What is the purpose of the TLS Handshake?

### ✅ Answer

The TLS Handshake establishes a secure encrypted connection before any HTTP data is transmitted.

---

## Question 41

### Does the Browser create the HTTP Request?

### ✅ Answer

Yes.

The Browser builds the complete HTTP Request before sending it to the Server.

---

## Question 42

### Does the Browser stop working after sending the Request?

### ✅ Answer

No.

After receiving the Response, it parses HTML, downloads CSS and JavaScript, builds the DOM, and renders the page.

---

## Question 43

### Does one webpage always generate one HTTP Request?

### ✅ Answer

No.

A single webpage may generate dozens or even hundreds of HTTP Requests.

Examples include:

- HTML
- CSS
- JavaScript
- Images
- Fonts
- API Calls

---

## Question 44

### Are DNS, TCP, and TLS part of ASP.NET Core?

### ✅ Answer

No.

They are Networking concepts.

Every ASP.NET Core application depends on them, but they are not implemented by ASP.NET Core itself.

---

## Question 45

### What is the final step performed by the Browser before the Request leaves the Client?

### ✅ Answer

Sending the HTTP Request to the destination Server.

---

# Part 04 — HTTP Request

---

## Question 46

### What is an HTTP Request?

### ✅ Answer

An HTTP Request is a message sent by the Client asking the Server to perform an operation.

---

## Question 47

### What are the three main parts of an HTTP Request?

### ✅ Answer

An HTTP Request consists of:

- Request Line
- Headers
- Body (Optional)

---

## Question 48

### What is the Request Line?

### ✅ Answer

The first line of the HTTP Request.

It contains:

- HTTP Method
- Request Target (Path)
- HTTP Version

---

## Question 49

### What information does the Request Line contain?

### ✅ Answer

- Method
- Path
- HTTP Version

Example:

```http
GET /books HTTP/1.1
```

---

## Question 50

### What is the purpose of the HTTP Method?

### ✅ Answer

It tells the Server what operation the Client wants to perform.

Examples:

- Read
- Create
- Update
- Delete

---

## Question 51

### What is the purpose of the Path?

### ✅ Answer

The Path identifies the requested Resource on the Server.

Example:

```
/books/15
```

---

## Question 52

### Why is the HTTP Version included?

### ✅ Answer

It tells both the Client and the Server which HTTP specification should be used during communication.

---

## Question 53

### What are Headers?

### ✅ Answer

Headers contain metadata describing the Request.

They do not contain the actual business data.

---

## Question 54

### What is the Request Body?

### ✅ Answer

The Body contains the actual data being sent to the Server.

Example:

```json
{
    "title":"Clean Code"
}
```

---

## Question 55

### Does every HTTP Request contain a Body?

### ✅ Answer

No.

GET Requests usually do not contain a Body, while POST, PUT, and PATCH commonly do.

---

## Question 56

### Who creates the HTTP Request?

### ✅ Answer

The Browser or any HTTP Client creates the HTTP Request.

ASP.NET Core never creates Requests.

---

## Question 57

### Is the URL the same as the HTTP Request?

### ✅ Answer

No.

The URL is only one part of the HTTP Request.

The Request also contains:

- Method
- Headers
- Body
- HTTP Version

---

## Question 58

### Can applications other than Browsers send HTTP Requests?

### ✅ Answer

Yes.

Examples include:

- Postman
- Mobile Applications
- Desktop Applications
- IoT Devices

---

## Question 59

### Is HTTP specific to Browsers?

### ✅ Answer

No.

HTTP is a general communication protocol used by any HTTP Client.

---

## Question 60

### What is the relationship between the Browser and the HTTP Request?

### ✅ Answer

The Browser analyzes the URL, builds the HTTP Request according to the HTTP Protocol, and then sends it to the Server.

---

# Part 05 — HTTP Methods

---

## Question 61

### What is an HTTP Method?

### ✅ Answer

An HTTP Method tells the Server what operation the Client wants to perform on a Resource.

---

## Question 62

### Name the five most common HTTP Methods.

### ✅ Answer

- GET
- POST
- PUT
- PATCH
- DELETE

---

## Question 63

### What is GET used for?

### ✅ Answer

GET is used to retrieve data from the Server.

It should not modify any data.

---

## Question 64

### What is POST used for?

### ✅ Answer

POST is used to create new Resources.

It usually contains a Request Body.

---

## Question 65

### What is PUT used for?

### ✅ Answer

PUT replaces an existing Resource completely with a new version.

---

## Question 66

### What is PATCH used for?

### ✅ Answer

PATCH updates only specific fields of an existing Resource.

---

## Question 67

### What is DELETE used for?

### ✅ Answer

DELETE removes an existing Resource from the Server.

---

## Question 68

### Why shouldn't GET modify data?

### ✅ Answer

Because GET is defined as a Safe Method.

Clients, Browsers, and Search Engines assume that GET Requests only retrieve information.

---

## Question 69

### What is the difference between PUT and PATCH?

### ✅ Answer

PUT replaces the entire Resource.

PATCH updates only part of the Resource.

---

## Question 70

### What is an Idempotent Method?

### ✅ Answer

An Idempotent Method produces the same final result even if executed multiple times.

Examples:

- GET
- PUT
- DELETE
---
# Part 06 — HTTP Headers

---

## Question 71

### What are HTTP Headers?

### ✅ Answer

HTTP Headers are metadata that provide additional information about an HTTP Request or Response.

They describe the message but do not contain the actual business data.

---

## Question 72

### Why do we need HTTP Headers?

### ✅ Answer

Headers provide additional information such as:

- Content Type
- Authentication
- Preferred Language
- Browser Information
- Cookies

Without Headers, the Server would not know how to process the Request correctly.

---

## Question 73

### What is the format of an HTTP Header?

### ✅ Answer

Every Header consists of a name and a value.

Example:

```http
Content-Type: application/json
```

---

## Question 74

### What is the difference between Request Headers and Response Headers?

### ✅ Answer

Request Headers are sent by the Client.

Response Headers are sent by the Server.

---

## Question 75

### What is the Host Header?

### ✅ Answer

The Host Header specifies the destination Server.

Example:

```http
Host: localhost:5001
```

It is required in HTTP/1.1.

---

## Question 76

### What is the User-Agent Header?

### ✅ Answer

The User-Agent Header identifies the Client application making the Request.

Example:

```http
User-Agent: Chrome
```

---

## Question 77

### What is the Accept Header?

### ✅ Answer

The Accept Header tells the Server which Response format the Client prefers.

Example:

```http
Accept: application/json
```

---

## Question 78

### What is the Accept-Language Header?

### ✅ Answer

The Accept-Language Header tells the Server which language the Client prefers.

Example:

```http
Accept-Language: en-US
```

---

## Question 79

### What is the Content-Type Header?

### ✅ Answer

Content-Type specifies the format of the Request Body.

Examples:

- application/json
- multipart/form-data
- application/xml

---

## Question 80

### What is the Authorization Header?

### ✅ Answer

The Authorization Header carries authentication credentials.

Example:

```http
Authorization: Bearer <token>
```

---

## Question 81

### What is the Cookie Header?

### ✅ Answer

The Cookie Header sends Cookies previously stored by the Browser back to the Server.

---

## Question 82

### What is the difference between Accept and Content-Type?

### ✅ Answer

Accept specifies the format the Client wants to receive.

Content-Type specifies the format of the data being sent.

---

## Question 83

### What is the difference between Headers and Body?

### ✅ Answer

Headers contain metadata.

The Body contains the actual business data.

---

## Question 84

### Why shouldn't authentication information be sent through the URL?

### ✅ Answer

Because URLs may be logged, cached, bookmarked, or exposed.

Authentication information should be sent using the Authorization Header.

---

## Question 85

### Are HTTP Headers specific to ASP.NET Core?

### ✅ Answer

No.

HTTP Headers are part of the HTTP Protocol and are used by every Web Framework.

---

# Part 07 — HTTP Body

---

## Question 86

### What is the HTTP Body?

### ✅ Answer

The HTTP Body contains the actual data sent between the Client and the Server.

---

## Question 87

### Does every Request contain a Body?

### ✅ Answer

No.

The Body is optional.

GET Requests usually have no Body.

POST, PUT, and PATCH usually contain one.

---

## Question 88

### Why doesn't GET usually contain a Body?

### ✅ Answer

Because GET is used to retrieve data.

The required information is usually available in the URL and Query String.

---

## Question 89

### Which HTTP Methods usually contain a Body?

### ✅ Answer

- POST
- PUT
- PATCH

---

## Question 90

### Name the most common Body formats.

### ✅ Answer

- JSON
- Form URL Encoded
- Multipart Form Data
- XML
- Plain Text

---

## Question 91

### Which Body format is most common in modern APIs?

### ✅ Answer

JSON.

---

## Question 92

### Why is Content-Type important?

### ✅ Answer

Content-Type tells the Server how to interpret and parse the Request Body.

---

## Question 93

### What happens if Content-Type is incorrect?

### ✅ Answer

The Server may fail to parse the Body correctly, resulting in validation or parsing errors.

---

## Question 94

### Can the Body contain files?

### ✅ Answer

Yes.

Files are commonly sent using multipart/form-data.

---

## Question 95

### What is the relationship between Content-Type and Body?

### ✅ Answer

Content-Type describes the format of the Body.

The Server reads Content-Type before parsing the Body.

---

# Part 08 — HTTP Response

---

## Question 96

### What is an HTTP Response?

### ✅ Answer

An HTTP Response is the message returned by the Server after processing an HTTP Request.

---

## Question 97

### What are the three parts of an HTTP Response?

### ✅ Answer

- Status Line
- Headers
- Body

---

## Question 98

### What is the Status Line?

### ✅ Answer

The first line of an HTTP Response.

Example:

```http
HTTP/1.1 200 OK
```

It contains:

- HTTP Version
- Status Code
- Status Message

---

## Question 99

### What is contained inside the Response Body?

### ✅ Answer

The Response Body contains the actual data returned by the Server.

Examples include:

- HTML
- JSON
- Images
- CSS
- JavaScript
- PDF
- Files

---

## Question 100

### Does every Response contain HTML?

### ✅ Answer

No.

The Response may contain any type of content depending on the requested resource.

---

## Question 101

### What are Response Headers?

### ✅ Answer

Response Headers provide additional information about the Server's Response.

Examples include:

- Content-Type
- Content-Length
- Cache-Control
- Set-Cookie

---

## Question 102

### Why does the Browser read the Status Code before the Body?

### ✅ Answer

Because it must first determine whether the Request succeeded before processing the returned data.

---

## Question 103

### What does the Browser do after receiving the Response?

### ✅ Answer

The Browser:

- Reads the Status Code.
- Reads the Headers.
- Reads the Body.
- Renders the returned content.

---

## Question 104

### Can an HTTP Response return JSON?

### ✅ Answer

Yes.

JSON is commonly returned by Web APIs.

---

## Question 105

### Are HTTP Responses standardized?

### ✅ Answer

Yes.

Every Web Server follows the HTTP standard when creating Responses.
---
# Part 09 — HTTP Status Codes

---

## Question 106

### What is an HTTP Status Code?

### ✅ Answer

An HTTP Status Code is a three-digit number returned by the Server to indicate the result of processing an HTTP Request.

---

## Question 107

### Why do we need Status Codes?

### ✅ Answer

Status Codes allow the Client to determine whether the Request succeeded, failed, or requires another action.

---

## Question 108

### What are the five Status Code categories?

### ✅ Answer

- 1xx → Informational
- 2xx → Success
- 3xx → Redirection
- 4xx → Client Errors
- 5xx → Server Errors

---

## Question 109

### What does 1xx mean?

### ✅ Answer

Informational responses.

The Server has received the Request and processing is continuing.

---

## Question 110

### What does 2xx mean?

### ✅ Answer

The Request completed successfully.

---

## Question 111

### What does 3xx mean?

### ✅ Answer

The Client must perform another action, usually following a Redirect.

---

## Question 112

### What does 4xx mean?

### ✅ Answer

The Request contains an error caused by the Client.

---

## Question 113

### What does 5xx mean?

### ✅ Answer

The Request reached the Server successfully, but the Server failed while processing it.

---

## Question 114

### What does 200 OK mean?

### ✅ Answer

The Request completed successfully.

---

## Question 115

### What does 201 Created mean?

### ✅ Answer

A new Resource has been created successfully.

Usually returned after a successful POST Request.

---

## Question 116

### What does 204 No Content mean?

### ✅ Answer

The Request succeeded, but the Server has no content to return.

---

## Question 117

### What does 301 Mean?

### ✅ Answer

The requested Resource has been permanently moved to a new location.

---

## Question 118

### What does 302 Mean?

### ✅ Answer

The requested Resource is temporarily available at another location.

---

## Question 119

### What does 400 Bad Request mean?

### ✅ Answer

The Request is invalid or malformed.

---

## Question 120

### What does 401 Unauthorized mean?

### ✅ Answer

Authentication is required.

The Client has not successfully authenticated.

---

## Question 121

### What does 403 Forbidden mean?

### ✅ Answer

The Client is authenticated, but does not have permission to access the requested Resource.

---

## Question 122

### What does 404 Not Found mean?

### ✅ Answer

The requested Resource does not exist.

---

## Question 123

### What does 500 Internal Server Error mean?

### ✅ Answer

The Server encountered an unexpected error while processing the Request.

---

## Question 124

### What does 503 Service Unavailable mean?

### ✅ Answer

The Server is temporarily unavailable due to maintenance or overload.

---

## Question 125

### What is the difference between 401 and 403?

### ✅ Answer

401 means the user has not been authenticated.

403 means the user is authenticated but does not have permission.

---

## Question 126

### What is the difference between 404 and 500?

### ✅ Answer

404 means the requested Resource does not exist.

500 means the Server encountered an internal error while processing the Request.

---

## Question 127

### Does every successful Request return 200?

### ✅ Answer

No.

Successful Requests may return:

- 200 OK
- 201 Created
- 204 No Content

depending on the operation performed.

---

# Part 10 — Chrome DevTools & Postman

---

## Question 128

### What is Chrome DevTools?

### ✅ Answer

Chrome DevTools is a set of tools built into the Browser that allows developers to inspect and debug web applications.

---

## Question 129

### Which tab is used to inspect HTTP Requests?

### ✅ Answer

The **Network** tab.

---

## Question 130

### What information can be found inside the Network tab?

### ✅ Answer

- Request URL
- HTTP Method
- Status Code
- Request Headers
- Response Headers
- Request Body
- Response Body
- Timing Information

---

## Question 131

### Does one webpage usually generate one Request?

### ✅ Answer

No.

A single webpage may generate dozens or hundreds of Requests.

---

## Question 132

### What is Postman?

### ✅ Answer

Postman is an HTTP Client used to create, send, and test HTTP Requests.

---

## Question 133

### Can Postman communicate with ASP.NET Core without a Browser?

### ✅ Answer

Yes.

Postman is itself an HTTP Client.

It communicates directly with the Server.

---

## Question 134

### Is HTTP limited to Browsers?

### ✅ Answer

No.

Any HTTP Client can communicate using the HTTP Protocol.

---

## Question 135

### Name some HTTP Clients.

### ✅ Answer

- Chrome
- Edge
- Firefox
- Postman
- Mobile Applications
- Desktop Applications

---

# Part 11 — Interview Questions

---

## Question 136

### Explain what happens after pressing Enter.

### ✅ Answer

The Browser:

- Reads the URL.
- Parses the URL.
- Checks the Cache.
- Resolves the Host using DNS.
- Opens a TCP Connection.
- Performs the TLS Handshake (HTTPS).
- Creates the HTTP Request.
- Sends the HTTP Request.

---

## Question 137

### Who creates the HTTP Request?

### ✅ Answer

The Browser or another HTTP Client.

ASP.NET Core never creates HTTP Requests.

---

## Question 138

### Who receives the HTTP Request first in ASP.NET Core?

### ✅ Answer

Kestrel.

---

## Question 139

### Does MVC receive the Request directly?

### ✅ Answer

No.

The Request first reaches Kestrel, then the ASP.NET Core Host, Middleware Pipeline, Routing, and finally MVC.

---

## Question 140

### Why can't two applications listen on the same IP Address and Port simultaneously?

### ✅ Answer

Because the operating system would not know which application should receive the incoming Request.

Each IP Address + Port combination can be owned by only one listening application at a time.

---

## Question 141

### Why does Kestrel listen on a Port?

### ✅ Answer

Because HTTP Requests arrive through Ports.

Listening means waiting for incoming network connections.

---

## Question 142

### What is the difference between a Process and a Program?

### ✅ Answer

A Program is an executable file stored on disk.

A Process is a running instance of that Program loaded into memory (RAM).

---

## Question 143

### What is a Socket?

### ✅ Answer

A Socket is an endpoint of network communication.

It represents the communication channel through which data flows between the Client and the Server.

---

## Question 144

### What is the relationship between IP Address, Port and Socket?

### ✅ Answer

The IP Address identifies the machine.

The Port identifies the application.

The Socket represents the communication endpoint used to exchange data.

---

## Question 145

### Why is the Browser considered a Client?

### ✅ Answer

Because it initiates communication by sending HTTP Requests to Servers.

---

# 🎓 Graduation Challenge

---

## Question 146

### Draw the complete Request Journey from pressing Enter until Kestrel receives the Request.

### ✅ Answer

```text
User
    │
    ▼
Browser
    │
    ▼
Read URL
    │
    ▼
Parse URL
    │
    ▼
Check Cache
    │
    ▼
DNS Lookup
    │
    ▼
TCP Connection
    │
    ▼
TLS Handshake
    │
    ▼
Create HTTP Request
    │
    ▼
Send HTTP Request
    │
    ▼
Internet
    │
    ▼
Kestrel
```

---

## Question 147

### Draw the HTTP Request structure.

### ✅ Answer

```text
HTTP Request

│

├── Request Line

├── Headers

└── Body
```

---

## Question 148

### Draw the HTTP Response structure.

### ✅ Answer

```text
HTTP Response

│

├── Status Line

├── Headers

└── Body
```

---

## Question 149

### Explain the complete Sprint 01 in your own words.

### ✅ Answer

The Browser starts by reading and parsing the URL.

It prepares the communication by resolving the Host, establishing a network connection, and creating an HTTP Request.

The Request follows the HTTP Protocol and contains a Request Line, Headers, and optionally a Body.

The Server processes the Request and returns an HTTP Response containing a Status Line, Headers, and optionally a Body.

The Browser then processes the Response and renders the final content.

---

## Question 150

### What is the most important lesson learned from Sprint 01?

### ✅ Answer

Before studying ASP.NET Core itself, it is essential to understand the complete HTTP communication process between the Client and the Server.

ASP.NET Core begins only after the HTTP Request reaches Kestrel.

---

# ✅ Sprint 01 Completed

After completing this Knowledge Check, you should be able to:

- Explain the complete HTTP Request lifecycle.
- Analyze any URL.
- Read HTTP Requests and Responses.
- Differentiate HTTP Methods.
- Understand Headers and Body.
- Interpret HTTP Status Codes.
- Use Chrome DevTools and Postman to inspect HTTP communication.
- Explain the complete journey from the Browser until the Request reaches Kestrel.

**You are now ready for Sprint 02 — Kestrel & Web Hosting Fundamentals.**
