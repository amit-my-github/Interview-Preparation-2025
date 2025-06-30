---

```markdown
# ASP.NET Core Study Topics

## Table of Contents

- [Application Structure and Organization](#application-structure-and-organization)
  - [ASP.NET Core MVC vs Razor Pages](#aspnet-core-mvc-vs-razor-pages)
  - [Areas in ASP.NET Core](#areas-in-aspnet-core)
  - [View Components in ASP.NET Core](#view-components-in-aspnet-core)
  - [Tag Helpers in ASP.NET Core](#tag-helpers-in-aspnet-core)

- [Middleware and Request Pipeline](#middleware-and-request-pipeline)
  - [ASP.NET Core Middleware](#aspnet-core-middleware)
  - [Filters in ASP.NET Core](#filters-in-aspnet-core)
  - [Configure ASP.NET Core to work with proxy servers and load balancers](#configure-aspnet-core-to-work-with-proxy-servers-and-load-balancers)
  - [Access HttpContext in ASP.NET Core](#access-httpcontext-in-aspnet-core)

- [Security](#security)
  - [ASP.NET Core Authentication](#aspnet-core-authentication)
  - [Authorization in ASP.NET Core](#authorization-in-aspnet-core)
  - [Prevent Cross-Site Request Forgery (XSRF/CSRF) attacks in ASP.NET Core](#prevent-cross-site-request-forgery-xsrfcsrf-attacks-in-aspnet-core)
  - [Prevent Cross-Site Scripting (XSS) in ASP.NET Core](#prevent-cross-site-scripting-xss-in-aspnet-core)
  - [Prevent open redirect attacks in ASP.NET Core](#prevent-open-redirect-attacks-in-aspnet-core)
  - [Enforce HTTPS in ASP.NET Core](#enforce-https-in-aspnet-core)
  - [Configure ASP.NET Core Data Protection](#configure-aspnet-core-data-protection)

- [Dependency Injection and Configuration](#dependency-injection-and-configuration)
  - [Dependency injection in ASP.NET Core](#dependency-injection-in-aspnet-core)
  - [Configuration in ASP.NET Core](#configuration-in-aspnet-core)
  - [Safe storage of app secrets in development in ASP.NET Core](#safe-storage-of-app-secrets-in-development-in-aspnet-core)
  - [Use multiple environments in ASP.NET Core](#use-multiple-environments-in-aspnet-core)

- [Globalization and Localization](#globalization-and-localization)
  - [Globalization and localization in ASP.NET Core](#globalization-and-localization-in-aspnet-core)

- [Model Binding and Validation](#model-binding-and-validation)
  - [Model Binding in ASP.NET Core](#model-binding-in-aspnet-core)
  - [Custom Model Binding in ASP.NET Core](#custom-model-binding-in-aspnet-core)
  - [Model validation in ASP.NET Core MVC](#model-validation-in-aspnet-core-mvc)

- [State and Session Management](#state-and-session-management)
  - [Session and state management in ASP.NET Core](#session-and-state-management-in-aspnet-core)

- [Networking and HTTP](#networking-and-http)
  - [Make HTTP requests using IHttpClientFactory in ASP.NET Core](#make-http-requests-using-ihttpclientfactory-in-aspnet-core)

- [Static Content and Assets](#static-content-and-assets)
  - [Static files in ASP.NET Core](#static-files-in-aspnet-core)
  - [Bundle and minify static assets in ASP.NET Core](#bundle-and-minify-static-assets-in-aspnet-core)

- [Hosting and Servers](#hosting-and-servers)
  - [Host ASP.NET Core on Windows with IIS](#host-aspnet-core-on-windows-with-iis)
  - [Kestrel web server implementation in ASP.NET Core](#kestrel-web-server-implementation-in-aspnet-core)

- [Logging and Monitoring](#logging-and-monitoring)
  - [Logging in .NET Core and ASP.NET Core](#logging-in-net-core-and-aspnet-core)

- [CORS and External Access](#cors-and-external-access)
  - [Enable Cross-Origin Requests (CORS) in ASP.NET Core](#enable-cross-origin-requests-cors-in-aspnet-core)

- [Error Handling](#error-handling)
  - [Handle errors in ASP.NET Core](#handle-errors-in-aspnet-core)

- [Caching](#caching)
  - [Caching in ASP.NET Core](#caching-in-aspnet-core)

---

### Application Structure and Organization

#### ASP.NET Core MVC vs Razor Pages

#### Areas in ASP.NET Core

#### View Components in ASP.NET Core

#### Tag Helpers in ASP.NET Core

---

### Middleware and Request Pipeline

#### ASP.NET Core Middleware

#### Filters in ASP.NET Core

#### Configure ASP.NET Core to work with proxy servers and load balancers

#### Access HttpContext in ASP.NET Core

---

### Security

#### ASP.NET Core Authentication

#### Authorization in ASP.NET Core

#### Prevent Cross-Site Request Forgery (XSRF/CSRF) attacks in ASP.NET Core

#### Prevent Cross-Site Scripting (XSS) in ASP.NET Core

#### Prevent open redirect attacks in ASP.NET Core

#### Enforce HTTPS in ASP.NET Core

#### Configure ASP.NET Core Data Protection

---

### Dependency Injection and Configuration

#### Dependency injection in ASP.NET Core

#### Configuration in ASP.NET Core

#### Safe storage of app secrets in development in ASP.NET Core

#### Use multiple environments in ASP.NET Core

---

### Globalization and Localization

#### Globalization and localization in ASP.NET Core

---

### Model Binding and Validation

#### Model Binding in ASP.NET Core

#### Custom Model Binding in ASP.NET Core

#### Model validation in ASP.NET Core MVC

---

### State and Session Management

#### Session and state management in ASP.NET Core

---

### Networking and HTTP

#### Make HTTP requests using IHttpClientFactory in ASP.NET Core

---

### Static Content and Assets

#### Static files in ASP.NET Core

#### Bundle and minify static assets in ASP.NET Core

---

### Hosting and Servers

#### Host ASP.NET Core on Windows with IIS

#### Kestrel web server implementation in ASP.NET Core

---

### Logging and Monitoring

#### Logging in .NET Core and ASP.NET Core

---

### CORS and External Access

#### Enable Cross-Origin Requests (CORS) in ASP.NET Core

---

### Error Handling

#### Handle errors in ASP.NET Core

---

### Caching

#### Caching in ASP.NET Core
```

## ✅ **Interview-Ready Questions on ASP.NET Core, Proxies, and Kestrel**

### 🔹 **Understanding the Architecture**

1. **In real-world deployments, do ASP.NET Core applications run behind reverse proxies, load balancers, or both?**
2. **What roles do reverse proxies like NGINX and load balancers like AWS ELB play in a typical ASP.NET Core deployment?**

---

### 🔹 **Forwarded Headers and Middleware**

3. **Why is it important to configure `UseForwardedHeaders()` in ASP.NET Core applications running behind proxies?**
4. **What headers are commonly added by reverse proxies that ASP.NET Core needs to handle?**
5. **What happens if `UseForwardedHeaders()` is not configured in an ASP.NET Core application?**
6. **Does Kestrel still process requests if forwarded headers are not configured? What are the consequences?**
7. **How does `UseForwardedHeaders()` improve the accuracy of client-related data like IP address and HTTPS detection?**

---

### 🔹 **Configuration and Security**

8. **How do you configure `ForwardedHeadersOptions` in ASP.NET Core?**
9. **Why is it important to restrict `KnownProxies` or `KnownNetworks` when using forwarded headers?**
10. **What potential security risks exist if forwarded headers are trusted without proper validation?**

---

### 🔹 **Development vs Production**

11. **Do you need to configure forwarded headers in a local development environment? Why or why not?**
12. **When would it make sense to simulate a proxy locally during development?**
13. **What’s the difference in behavior between local Kestrel traffic and proxied traffic in production?**

---

### 🔹 **Middleware Pipeline and Execution**

14. **Where should `UseForwardedHeaders()` be placed in the ASP.NET Core middleware pipeline?**
15. **What middleware behaviors depend on accurate protocol or IP detection in ASP.NET Core (e.g., HTTPS redirection, authentication)?**

---

### 🔹 **Big Picture & Best Practices**

16. **Can you describe the complete request flow from client to Kestrel, including NGINX and forwarded headers?**
17. **What are best practices for deploying ASP.NET Core behind NGINX or other reverse proxies?**
18. **How do you troubleshoot incorrect protocol or IP detection in an ASP.NET Core app behind a proxy?**

---
