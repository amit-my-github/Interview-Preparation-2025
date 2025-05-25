# What is a preflight request?
# What is CORS?
# What is OWIN?
# What is Middleware?
# OAuth 2.0 using the Client Credentials flow
# How is throttling implemented in your system?
# How do you handle security around token expiration and refresh tokens?

Web API project NuGet package list — this is a solid and modern ASP.NET Web API on .NET Framework 4.8 setup, with features for authentication, CORS, logging, DI, Swagger, rate limiting, and more.
To help with knowledge retention and interview prep, here's a clean breakdown of the key technologies and how you can talk about them

✅ High-Level Project Insights
▶️ Type: ASP.NET Web API
🏗 Framework: .NET Framework 4.8
🔐 Auth: JWT, OAuth, ASP.NET Identity
📦 DI/IoC: StructureMap
📘 Docs: Swagger via Swashbuckle
📊 Monitoring: New Relic + log4net
🌐 Cross-Origin: CORS + OWIN Middleware
🔒 Rate Limiting: WebApiThrottle

# What is a preflight request?

A preflight request is a OPTIONS HTTP request sent by the browser before the actual API request, to check if the actual request is allowed.The purpose of this is to ensure that the server is willing to accept the cross-origin request and that it allows certain methods, headers, etc.

# What is CORS?

CORS (Cross-Origin Resource Sharing) is a security feature enforced by browsers.
It controls whether a web application running at one origin (domain) is allowed to make requests to a server hosted on a different origin.
# Why is it needed?
By default, browsers block cross-origin AJAX requests for security reasons (to prevent malicious sites from stealing data from another domain).
CORS provides a controlled way to whitelist trusted domains so they can call your APIs


# What is OWIN?

OWIN stands for **Open Web Interface for .NET**. It is a specification that defines a standard interface between .NET web applications and web servers (like IIS, Kestrel, etc.).

**In simple terms:**

* OWIN provides a way to decouple the web application from the web server.
* It allows you to run .NET web applications on different types of servers.
* It enables flexibility to add custom middleware to handle various concerns, like authentication, logging, routing, etc.

For example, OWIN allows you to build and configure your own pipeline of logic for HTTP requests and responses without relying on the built-in IIS pipeline.

# What is Middleware?

Middleware is a piece of code that handles the request and response processing in an application. Middleware components are executed in a sequence and can modify the request or response, or perform some task before passing control to the next middleware.

**In simple terms:**

* Middleware is like a **processing step** that sits in between the client request and the server's response.
* Each piece of middleware in the OWIN pipeline performs a specific task, such as authentication, logging, authorization, etc.
* Once one middleware finishes its task, it can pass the request to the next middleware, or it can stop the request if necessary (e.g., returning an error or a response).

### **Example of Middleware Tasks:**

1. **Authentication Middleware**: Checks if the user is logged in and provides the request with a user identity.
2. **Logging Middleware**: Logs each request to a file or database.
3. **CORS Middleware**: Handles Cross-Origin Resource Sharing (CORS) to allow or block certain domains from making requests.
4. **Compression Middleware**: Compresses the response data before sending it to the client.

### **OWIN and Middleware Working Together:**

In an OWIN-based application, you set up a pipeline of middleware that will handle incoming HTTP requests. The OWIN framework makes it easy to add or remove middleware as needed to customize the behavior of your application.

**Summary:**

* **OWIN** = Standard interface between web applications and web servers.
* **Middleware** = Custom processing steps that modify or handle HTTP requests and responses.


# Can you explain how authentication works in your Web API project?

Sure. In our Web API, we implemented OAuth 2.0 using the Client Credentials flow with JWT tokens for authentication.

Each company in our system is issued a unique Client ID and Client Secret — this is generated through the admin panel. When a company wants to consume our APIs, they first request a token by calling the /token endpoint with their credentials.

Internally, the token is issued using OAuthAuthorizationServerOptions where we customized the Provider to use ClientCredentialsAuthorizationServerProvider. This provider authenticates the client by validating their client ID and secret against our records and ensures the client has access to the requested subsite.

If validation is successful, we create a JWT token using a custom implementation of JwtAccessTokenFormat and return it in the response. This token is then sent by the client in the Authorization: Bearer <token> header for subsequent API calls.

To verify the token, we configured UseJwtBearerAuthentication in the OWIN pipeline. We also included additional headers for CORS support and to support multiple subsites and languages, we added custom headers like x-subsitecode and language.

While the system is secure and uses proper token expiration, one improvement we noted was that some endpoints weren’t using the [Authorize] attribute, which means protection wasn’t always enforced. We’ve started applying it globally or per-controller to restrict access properly.


# Can you explain how authentication works in your Web API project? Shot answers
We used the OAuth 2.0 client credentials flow, where each company gets a client ID and secret. They call our /token endpoint, and if their credentials are valid, we generate a JWT token and return it.

This token is then passed with each API request in the Authorization header. Our OWIN middleware handles the token validation using UseJwtBearerAuthentication, so only authenticated clients can access protected endpoints

# How is throttling implemented in your system?

In our system, throttling is implemented using the WebApiThrottle middleware. It's configured via web.config, where we define global rate limits and endpoint-specific rules. We use IP-based throttling to control how many requests a client can make — for example, 30 requests per second and 200 per minute by default. For certain high-traffic endpoints like health/getstatus, we've configured custom limits, such as 1000 requests per second.

The middleware tracks incoming requests in memory and enforces these limits by returning HTTP 429 (Too Many Requests) responses when thresholds are exceeded. This helps us protect the API from abuse, maintain performance, and ensure fair usage across clients.

# How do you handle security around token expiration and refresh tokens?

In our implementation of OAuth 2.0 Client Credentials flow, we only issue short-lived access tokens — for example, tokens that expire in 24hours. Since this is a machine-to-machine flow, we don’t use refresh tokens.

Instead, clients are expected to use their clientId and clientSecret to request a new token when the old one expires. This keeps the system simple and secure, since it avoids the complexity of storing and validating refresh tokens.

We also limit failed login attempts, log token-related events (success/failure), and rotate client secrets periodically to maintain long-term security.

In case a token or secret is suspected to be compromised, we can immediately revoke access by disabling the client or rotating their secret in the admin interface.

# How is the token stored on the client?

From the Web API side, we issue the access token after validating the client credentials. The client is responsible for securely storing and managing that token — whether in memory, cookies, or local storage — depending on its platform and security requirements

✅ Topics You've Already Covered (Great!)

    ✅ What is a Preflight request

    ✅ What is CORS

    ✅ What is OWIN

    ✅ What is Middleware

    ✅ OAuth 2.0 using the Client Credentials Flow

    ✅ Throttling and rate limiting

    ✅ Token expiration and refresh (partially)

✅ Remaining/Recommended Topics to Cover

Here’s what you should add to be fully prepared:
🔐 Authentication & Authorization

    ✅ OAuth 2.0 — covered

    🔲 Refresh tokens (you partially touched this, but go deeper)

    🔲 How to use [Authorize] attribute

    🔲 Role-based authorization vs claims-based

    🔲 ASP.NET Identity vs custom authentication

    🔲 Cookie authentication vs Token authentication (esp. in MVC vs API)

🏗️ ASP.NET Web API (Full Framework)

    🔲 Routing (WebApiConfig, AttributeRouting)

    🔲 Model Binding vs Parameter Binding

    🔲 Filters: Action filters, Exception filters

    🔲 Content Negotiation (JSON/XML)

    🔲 Dependency Injection (StructureMap, Unity, etc.)

    🔲 Using HttpClient for consuming APIs

    🔲 Return types: IHttpActionResult, HttpResponseMessage

🆕 ASP.NET Core Specific Topics

    🔲 Differences between ASP.NET Web API (Full) and ASP.NET Core

    🔲 Built-in dependency injection in Core

    🔲 Startup.cs – ConfigureServices, Configure methods

    🔲 Middleware order in Core

    🔲 Using app.UseAuthentication() and app.UseAuthorization()

    🔲 Minimal APIs in .NET 6+

    🔲 Configuration & AppSettings (appsettings.json)

    🔲 Logging (Serilog, built-in logging, etc.)

⚙️ API Design & Best Practices

    🔲 REST principles (GET, POST, PUT, DELETE)

    🔲 Versioning APIs

    🔲 API documentation using Swagger / Swashbuckle

    🔲 Pagination, filtering, sorting

    🔲 Error handling and global exception handling

    🔲 Returning consistent API responses

📊 Database & Data Access

    🔲 EF vs EF Core (differences)

    🔲 Code-first vs Database-first

    🔲 Async programming with EF

    🔲 Stored Procedures & Dapper

    🔲 Transactions in Web API

⚙️ Security & Production Concerns

    🔲 HTTPS enforcement

    🔲 CORS misconfigurations

    🔲 Token storage (local storage vs cookies)

    🔲 Preventing CSRF and XSS

    🔲 Protecting sensitive endpoints

    🔲 Logging & Monitoring (e.g., New Relic, App Insights)

⚡ Optional (Advanced)

    🔲 Rate limiting in ASP.NET Core using middleware (not WebApiThrottle)

    🔲 Background tasks with IHostedService

    🔲 API Gateway basics (e.g., YARP, Ocelot)

    🔲 gRPC or SignalR (real-time APIs)