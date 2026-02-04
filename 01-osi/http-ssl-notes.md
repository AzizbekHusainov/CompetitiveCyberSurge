# Actually here
**Protocols**

A set of rules computers follow to communicate.

In competition, the protocol tells you how to interact with a service.

\-            **HTTP/HTTPS** — web apps and APIs

\-            **FTP** — file transfers (upload/download)

 

**URI vs URL**

URI (Uniform Resource Identifier): a general identifier for a resource.

URL (Uniform Resource Locator): a type of URI that includes where the resource is and how to access it.

**Important:** All URLs are URIs, but not all URIs are URLs

Example URL:

[https://example.com/login](https://example.com/login)

\- **https**  
\- **example.com** \=  
\- **/login** \= path (endpoint)

**URI Structure**

scheme://authority/path?query\#fragment

\-            scheme — protocol (https)

\-            authority — host/server

\-            path — endpoint (/profile)

\-            query — parameters (?id=3)

\-            fragment — client-side only (\#settings, not sent to server)

Why URI matters in competition

\-            Query parameters are a primary attack surface (IDOR, data exposure).

\-            Changing paths can reveal hidden endpoints (/admin, /debug).

\-            Fragments are ignored by the server — common beginner trap.

\-            Encoded URIs may bypass filters.

What to try with every URI

\-            Change path

\-            Change parameter values

\-            Remove parameters

\-            Add new parameters

\-            Try encoded version

**HTTP Headers**

HTTP headers allow the client and server to send additional information with an HTTP request or response. They consist of (metadata) a name–value pair separated by a colon (for example, Allow: POST). Header names are case-insensitive, and in newer HTTP versions headers are displayed in lowercase, with some special pseudo-headers prefixed by a colon (such as :status: 200). [HTTP headers \- HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers)

\-            Headers be grouped according to their context (request, response, representation, payload headers) or by how proxies handle them (end-to-end and hop-by-hop) .

\-            Table of header fields can be found here [HTTP headers can be found on Wikipedia](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Request_fields). ***USE “CTRL \+ F” to easy search.***

Why headers matter in NCL:

\-             Tokens/credentials may be in headers (auth).

\-             Server behavior can change based on headers.

\-            Misconfigurations can leak info (sometimes even flags).

Common headers to recognize:

\-            **Authorization:** Bearer tokens / credentials

\-            **Cookie:** session identifiers

\-            **Content-Type:** format of sent data (JSON, form data)

\-            **Allow:** methods the endpoint accepts (GET, POST, etc.)

\-            **User-Agent**: client info (occasionally used for blocking/logic)

 

**HTTP Methods: GET and POST**

**GET**

GET means “give me something.” It requests data and should not change server state. GET parameters are usually visible in the URL.

**Example:**

GET /profile?id=3

Why GET matters in competition:

\-            Parameters are easy to change (common source of data exposure).

\-            Authorization mistakes often show up here (e.g., viewing other users’ data).

What to try when you see GET:

\-            Change parameter values: id=1 → id=2 → id=0

\-            Try removing parameters entirely.

\-            Add a suspicious parameter: admin=true

\-            Change the path: /profile → /admin → /debug

\-            Try adding headers (especially Authorization) if you have a token.

**curl examples (GET):**

curl http://site.com/profile?id=1

curl \-H "Authorization: Bearer token123" http://site.com/profile?id=1

 

**POST**

POST means “send this data.” It submits data to the server and is commonly used for logins, forms, and uploads. POST data is usually in the request body (not visible in the URL).

**Why POST matters in competition:**

\-            Login/auth flows often rely on POST.

\-            You can intercept and modify submitted fields.

\-            Servers sometimes trust client-supplied fields too much.

What to try when you see POST:

\-            Change submitted values (usernames, roles, IDs).

\-            Add extra fields (e.g., isAdmin=true).

\-            Remove fields (see if validation is weak).

\-            Replay the request with small changes; compare responses.

**curl examples (POST):**

curl \-X POST \-d "username=admin\&password;=test" http://site.com/login

curl \-X POST \-H "Content-Type: application/json" \-d '{"user":"admin"}'

[http://site.com/profile](http://site.com/profile)

**Comparison:**

GET                                                                             	     	POST

| Retrieve Data | Send Data |
| :---- | :---- |
| Parameters often in URLs | Data typically request in body |
| Easy to tamper via URL | Best tested by intercept/replay |
| Common: ID/parameter mistakes | Common: auth/form mistakes |

 

**FTP and Equivalents**

FTP (File Transfer Protocol) is used to upload/download files. In challenges, check for misconfigurations.

Things to check:

\-            Anonymous login enabled

\-            Directory listing shows interesting files

\-            Write access (uploads) is allowed

**FTP command equivalents:**

\-            RETR — download a file (**GET equivalent**)

\-            STOR — upload a file (**POST equivalent**)

 

**Challenge Checklist**

\-            Inspect URLs and modify paths/parameters

\-            Read request/response headers carefully (tokens, Allow, cookies)

\-            Change GET parameters and compare responses

\-            Intercept/replay POST requests and modify fields

\-            If FTP exists: list files immediately; test RETR/STOR

Remember: Web challenges are conversations. Headers and methods tell you how to talk back

 

 

 

 

 

 

 

 

**Questions**

**1\. What HTTP request header is used to denote what URI linked to the resource being requested?**

The description for this header is, “This is the address of the previous web page from which a link to the currently requested page was followed.”

⚠️

Note that the official specification has the name for this header spelled incorrectly. The correct answer should use the incorrect spelling from the specification.

**2\. What HTTP request header is used to identify the client software that made the HTTP request?**

The description for this header is, “The user agent string of the user agent.”

USER AGENT HEADER

**3\. What HTTP request header is used to identify the acceptable content types that can be returned?**

The description for this header is, “Media type(s) that is/are acceptable for the response. See Content negotiation.

 ACCEPT HEADER Field
