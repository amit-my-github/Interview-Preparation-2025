Interview-Ready Version (Project Story Format)
1) 12 years at Legal Intelligence – Legal search platform integrating data from 25+ publishers.
2) Technology Used – Used ASP.NET MVC 5, Web API, and SQL Server.
3) Full Development Cycle – Coding, unit tests, code reviews, deployments.
4) Architecture Revamp – Led revamping code architecture for performance and maintainability.
5) Technical Growth – Integrated Solr and used JavaScript frameworks for responsive UIs.
6) Client Visits – Represented team in 2019 and 2022, gathering user feedback.
7) Innovation Camp – Participated in Wolters Kluwer’s Innovation Camp in the Netherlands.
8) Team Recognition – Best Team Awards in 2017 and 2024.
9) Personal Recognition – Acknowledged in 2015 for architecture revamp; received CMD R&R Award.
10) Fulfillment – A rewarding experience combining technical work and growth.

1)INTRO: I was part of a major legal tech platform called Legal Intelligence for over 12 years. It’s a legal search platform that helps professionals access legal and fiscal content quickly, integrating data from over 25 major publishers like Wolters Kluwer and Sdu.

2)TOOLS: I worked on the frontend team, using ASP.NET MVC 5, Web API, SQL Server, Apache solr  to build the core user experience. 

3)ROLE: I was involved in the entire development cycle—understanding user requirements, coding, writing unit tests, participating in code reviews, and deploying. I also played a key role in revamping the code architecture to improve performance and maintainability.

3)SOLR EXPERIENCE:  Along the way, I gained valuable experience integrating Solr for complex search functionality and using JavaScript frameworks to build responsive, user-friendly interfaces. These experiences helped me grow as a full-stack developer, focusing on performance, usability, and scalability.

4)CLIENT VISIT: Beyond coding, I represented the team during client visits in 2019 and 2022, contributing to on-site implementation and gathering direct feedback. These opportunities helped me grow professionally, particularly in team coordination and client communication.

5)Innovation CAMP: I also participated in Wolters Kluwer’s Innovation Camp in the Netherlands, which was an energizing experience that helped us think beyond our usual work.

6)Team Awards: Over the years, our team earned multiple recognitions, including Best Team Awards in 2017 and 2024. Personally, I was acknowledged in 2015 for leading a successful architecture revamp and was honored with a CMD R&R Award for my long-term contributions.

7)Fulfillment: Overall, it’s been one of the most fulfilling projects of my career, combining deep technical work, collaboration, real impact, and long-term growth.

	

	
	What were some challenges you faced and how did you overcome them?
	
	
	Working on Legal Intelligence for over 12 years taught me a lot — technically and beyond. From the tech side, I really deepened my skills in ASP.NET, MVC, Web API, and especially in integrating complex search systems like Solr. Since we were dealing with highly structured legal content, it forced me to think deeply about how to build a clean, responsive UI that could handle advanced search — and still be easy for non-technical users to use.”

    “One of the biggest challenges was scaling the system — not just in terms of traffic, but content. With over 25 publishers feeding data, and user expectations growing, we had to keep the frontend fast, modular, and stable, even while the backend systems kept evolving. It really pushed me to improve my architectural thinking, especially around decoupling components and optimizing for performance.”

    “Another challenge was understanding the legal domain itself. This wasn’t just about generic UI — it had to be precise, context-aware, and tailored to how legal professionals actually think. I had to work closely with the product team and even visit clients to see how they used the tool in real-life workflows. That changed how I approached feature design — we started thinking more in terms of user roles, personalized alerts, smart dossiers, and contextual content.”

    “On the softer side, I gained a lot in terms of collaboration and communication. Visiting clients in 2019 and 2022 really helped me connect user needs with technical solutions. And over time, I learned how to build systems that evolve — not just for today, but in a way that remains maintainable, scalable, and user-focused for the long term
	
LegalIntelligence Project Architecture:	
	
In LegalIntelligence project, we followed a Service-Oriented Architecture (SOA) to build modular and reusable services. To implement this, we used Windows Communication Foundation (WCF) as our core service framework. 

WCF was well-suited for SOA because it allowed us to expose services over multiple protocols — primarily HTTP for RESTful interfaces — while supporting features like message-level security, reliable messaging, and service contracts.

Each service was designed as an independent component, deployed via Windows Services, and exposed through WCF endpoints. 

This helped us maintain loose coupling, reuse services across multiple modules, and scale specific parts of the system without impacting the whole.

The front end was built using ASP.NET MVC for rendering views and handling user interactions.

Instead of having the MVC layer talk directly to the business logic or database, 
we introduced a middle layer - proxy service layer which is responsible to communicate — a self-hosted Web API using OWIN. This API acted as an abstraction layer and handled all communication between the UI and the business services.

We used a service proxy layer to abstract communication with our self-hosted Web API, which was built using OWIN. This approach allowed us to decouple our internal modules from the underlying HTTP implementation. The proxy encapsulated API endpoints, handled request building, and centralized error handling. As a result, the business logic stayed clean, testable, and resilient to changes in the API layer.

In our architecture, we followed a clear multi-layered structure. The front end was built with ASP.NET MVC, which consumed a self-hosted Web API using OWIN. This API acted as a gateway to the business layer."

"Our business layer resided on the application server and was responsible for implementing all core logic. It communicated with the database using Entity Framework, following the Repository and Unit of Work patterns to ensure clean separation of concerns, testability, and maintainability."

"This design allowed us to scale horizontally, keep each layer independently deployable and testable, and enforce domain boundaries. It also simplified onboarding and debugging, since each layer had a specific responsibility.

Our project follows a clean, multi-tier architecture. The front end is built in ASP.NET MVC and communicates with a self-hosted Web API using OWIN. This Web API acts as a boundary layer and interacts with our business logic, which resides on the application server."

"The business layer is where all core logic is implemented. We use Entity Framework with the Repository and Unit of Work patterns to access relational data from the SQL database."

"In addition to structured data, we also needed high-performance search functionality. For that, we integrated Apache Solr, which we accessed through a custom-built Solr client library. This allowed us to perform full-text search, faceted filtering, and dynamic sorting — features that would be inefficient in a traditional relational database."

"The Solr client was abstracted as part of our service layer so the rest of the application interacted with it like any other data source. This helped maintain loose coupling and kept our code clean and testable.

FINAL SCRIPT: 


