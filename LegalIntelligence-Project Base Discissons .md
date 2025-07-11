## About LegalIntelligence
Legal Intelligence is a comprehensive legal research and knowledge management platform built for law firms and legal departments. 
It combines smart search, advanced filtering, and a legal thesaurus to help lawyers find the most relevant legal content quickly — from public legal sources to over 5,000 publications from top Dutch legal publishers.

The platform also includes the LI Library, for digital access to your subscriptions, and the LI Catalog, which helps manage both paper and digital resources internally. Features like Single Sign-On, integration with existing systems, and a personalized dashboard make it a seamless and user-friendly tool for modern legal work. It’s one platform that brings together legal research, knowledge sharing, and library management — all in one place.

## What is the reason to stay in legal intelligence project so long?
I stayed with the Legal Intelligence project for over 12 years because it was a product with real purpose and constant growth.
The work was never repetitive — I kept learning new technologies, solving complex problems, and taking on more responsibility over time. 
I worked across the full development cycle, led key architecture improvements, and helped build a fast, reliable legal search platform. My experience with technologies like Solr, ASP.NET, and JavaScript made me a stronger full-stack developer. I also got the chance to represent the team during client visits and innovation events, which helped me grow professionally. 
The project gave me long-term growth, recognition, and a chance to make a real impact — that’s why I stayed.

## 🕒 LegalIntelligence — 2-Minute High-Level Overview

##  Legacy start
The LegalIntelligence project began in 2008, and when I joined the team, it was built using .NET Remoting for backend communication and ASPX pages for the UI, running on .NET Framework 2.0. That was a typical enterprise stack at the time.

## Architectural shift
As the system scaled and became more complex, we needed better modularity, scalability, and maintainability. Over the next few years, we evolved the architecture to adopt a Service-Oriented Architecture (SOA). We used WCF as the core framework, designing each service as an independent component hosted via Windows Services and exposed through WCF endpoints. This gave us loose coupling and allowed us to scale or update individual services without disrupting the entire system.

## Frontend
The frontend was migrated to ASP.NET MVC for better separation of concerns and a cleaner UI architecture. We added a service proxy layer between the UI and the backend, which communicated with a self-hosted OWIN-based Web API and deployed on the application server. This abstraction helped keep our business logic clean, testable, and resilient to API changes.

## Business layer
Our business layer, implemented all domain logic and connected to the database using Entity Framework, applying Repository and Unit of Work patterns. This ensured clean separation of concerns, simplified testing, and improved maintainability.

## Search
For high-performance search, we integrated Apache Solr using a custom client library, enabling full-text search, faceted filtering, and dynamic sorting — which wouldn’t have been efficient using only relational queries.

## Summary
Overall, this architectural evolution enabled us to scale horizontally, enforce domain boundaries, and keep the system flexible and maintainable over a 15+ year lifecycle — which was key to supporting continuous feature development in a complex legal domain.

## My Role 
My role included designing and implementing the backend service architecture, integrating Solr for search, and collaborating closely with the frontend team during the MVC migration.
---

## Authentication in Legal Intelligence

Legal Intelligence supports two main authentication flows.

First, most organizations use Single Sign-On (SSO) via SURFconext, a federated identity platform widely used by Dutch public institutions like courts, universities, and government bodies. This allows users to log in securely with their institutional credentials — no need for extra passwords. It’s centralized, user-friendly, and aligns with public sector IT policies.

For organizations that don’t use federated login, Legal Intelligence also supports a standard login form with username and password, providing secure access for smaller firms or external users.

While SURFconext is tailored to the Dutch public sector, platforms like Ping Identity serve private sector organizations. Ping Identity offers broader identity and access management features such as multi-factor authentication (MFA), API security, and hybrid cloud integration.

Legal Intelligence is flexible — it can integrate with both SURFconext and commercial solutions like Ping Identity through standard SAML or OIDC protocols, ensuring secure access across both public and private environments
email-based identity discovery for SSO

## Authorization in Legal Intelligence

RoleAuthorizationAttribute is a C# class that helps enforce access control based on user roles. It's applied to controller actions or entire controllers in an ASP.NET application and is commonly used in secure apps like Legal Intelligence to ensure only authorized users can perform sensitive operations

OR 

In Legal Intelligence, once a user is authenticated via SSO, ASP.NET stores their identity and roles in the user context. The app uses [Authorize] or [Authorize(Roles = "...")] attributes on controllers or actions to authorize access based on that information

## In short How Authentication and Authorization works in LegalIntelligence

The Legal Intelligence app uses SSO or Standard Login for authentication, session-based authentication to track user sessions across requests, and role-based authorization to ensure that users have access to the resources they’re authorized to use.


## 🔖 **Flashcard Points + Expanded Sentences**

| **Flashcard Point**                                                     
| ------------------------------------------------------------------------- 
| **Started with .NET Remoting and ASPX on .NET Framework 2.0**             
| **Scaled system needed better modularity → moved to SOA with WCF**        
| **Independent services via WCF endpoints and Windows Services**           
| **UI migrated to ASP.NET MVC for cleaner architecture**                   
| **Service proxy layer → OWIN-based Web API**                              
| **Business logic used Entity Framework with Repository & Unit of Work**   
| **Integrated Apache Solr for advanced search**                            
| **Architecture enabled horizontal scaling and long-term maintainability** 

---


Perfect — that extra detail makes your architecture even clearer and more robust. The fact that **communication from your ASP.NET MVC app to the application server is server-to-server** means:

---

### ✅ **You're Implementing a Distributed, Tiered Architecture**

Here's how that looks conceptually:

```
[ User Browser ]
       ↓
[ ASP.NET MVC Frontend (Web Server) ]
       ↓  (Server-to-Server HTTP Call)
[ OWIN Self-Hosted Web API (Application Server) ]
       ↓
[ Business Layer & EF (DLL inside API) ]
       ↓
[ Database Server ]
```

---

### 🔍 What This Server-to-Server Design Means

| Benefit          | Description                                                                                                              |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Security**     | Direct API access from browsers is avoided; only the MVC server talks to the API. This reduces surface area for attacks. |
| **Control**      | All frontend interaction goes through the MVC layer, making business flows easier to enforce and audit.                  |
| **Performance**  | Internal server-to-server calls can be optimized (e.g., connection pooling, internal networking).                        |
| **Scalability**  | You can scale the MVC web tier and application server independently, depending on load.                                  |
| **Future-ready** | This is a common architecture in enterprise systems — easily evolves into microservices or cloud-based services.         |

---





