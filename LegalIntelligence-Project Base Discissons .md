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

1) Introduction:
I worked on a major legal tech platform called Legal Intelligence for over 12 years. It’s a tool that helps legal and tax professionals quickly find information by searching through content from over 25 major publishers, including Wolters Kluwer and Sdu.

2) Tools & Technology:
I was part of the frontend development team, using tech stack like ASP.NET MVC 5, Web API, SQL Server, and Apache Solr to create the main user experience.

3) My Role:
I was involved in the full development process—understanding what users needed, writing code, testing it, reviewing other people’s code, and helping with deployment. I also helped redesign the code structure to make it faster and easier to maintain.

4) Solr Search Experience:
I gained strong experience using Apache Solr for advanced search features. I also worked with JavaScript frameworks to build fast, easy-to-use interfaces. This helped me grow as a full-stack developer, with a focus on performance, user experience, and scalability.

5) Client Interaction:
Besides development, I represented our team during client visits in 2019 and 2022. I helped with setting up the system on-site and collecting feedback. This helped me improve my skills in teamwork and communication with clients.

6) Innovation Camp:
I joined Wolters Kluwer’s Innovation Camp in the Netherlands, which gave me new ideas and helped me think creatively outside of my usual work.

7) Recognition & Awards:
Our team won several awards, including Best Team Awards in 2017 and 2024. I was personally recognized in 2015 for leading a successful system redesign and later received a CMD R&R Award for my long-term contributions to the project.

8) Fulfillment:
This project has been one of the most rewarding experiences of my career. It gave me the chance to work deeply on technical solutions, grow with a great team, and see the real impact of our work.
	

	
	What were some challenges you faced and how did you overcome them?
	
	
	Working on Legal Intelligence for over 12 years taught me a lot — technically and beyond. From the tech side, I really deepened my skills in ASP.NET, MVC, Web API, and especially in integrating complex search systems like Solr. Since we were dealing with highly structured legal content, it forced me to think deeply about how to build a clean, responsive UI that could handle advanced search — and still be easy for non-technical users to use.”

    “One of the biggest challenges was scaling the system — not just in terms of traffic, but content. With over 25 publishers feeding data, and user expectations growing, we had to keep the frontend fast, modular, and stable, even while the backend systems kept evolving. It really pushed me to improve my architectural thinking, especially around decoupling components and optimizing for performance.”

    “Another challenge was understanding the legal domain itself. This wasn’t just about generic UI — it had to be precise, context-aware, and tailored to how legal professionals actually think. I had to work closely with the product team and even visit clients to see how they used the tool in real-life workflows. That changed how I approached feature design — we started thinking more in terms of user roles, personalized alerts, smart dossiers, and contextual content.”

    “On the softer side, I gained a lot in terms of collaboration and communication. Visiting clients in 2019 and 2022 really helped me connect user needs with technical solutions. And over time, I learned how to build systems that evolve — not just for today, but in a way that remains maintainable, scalable, and user-focused for the long term
	
	Amit what is the reason to stay in legal intelligence project so long?
	
	I stayed with the Legal Intelligence project for over 12 years because it was a product with real purpose and constant growth.
	
	The work was never repetitive — I kept learning new technologies, solving complex problems, and taking on more responsibility over time. 
	I worked across the full development cycle, led key   architecture improvements, and helped build a fast, reliable legal search platform. 
	
	My experience with technologies like Solr, ASP.NET, and JavaScript made me a stronger full-stack developer. I also got the chance to represent the team during client visits and innovation events, which helped me grow professionally. 
	
	The project gave me long-term growth, recognition, and a chance to make a real impact — that’s why I stayed
	
LegalIntelligence Project Architecture: 
.NET Framework 2.0
SOA:
1) In LegalIntelligence project, we followed a Service-Oriented Architecture (SOA) to build modular and reusable services. 
To implement this, we used Windows Communication Foundation (WCF) as our core service framework. 
2) WCF was considered well-suited for SOA because it allowed us to expose services over multiple protocols — primarily HTTP for RESTful interfaces.
3) It also supported crucial features for service interaction like message-level security, reliable messaging, and service contracts
4) Each service was designed as an independent component, deployed via Windows Services, and exposed through WCF endpoints. 
5) This helped us maintain loose coupling, reuse services across multiple modules, and scale specific parts of the system without impacting the whole.

Front End:
6) The front end was built using ASP.NET MVC for rendering views and handling user interactions.

Service Proxy layer:
7) Instead of having the presentation layer talk directly to the business logic or database,
8) We used a service proxy layer to abstract communication with our self-hosted Web API, which was built using OWIN. 
9) This approach allowed us to decouple our internal modules from the underlying HTTP implementation. 
10)The proxy layer encapsulated API endpoints, handled request building, and centralized error handling. 
As a result, the business logic stayed clean, testable, and resilient to changes in the API layer.

Business Layer:
11) Our business layer resided on the application server and was responsible for implementing all core logic. 
It communicated with the database using Entity Framework, following the Repository and Unit of Work patterns to ensure clean separation of concerns, testability, and maintainability.
12) This design allowed us to scale horizontally, keep each layer independently deployable and testable, and enforce domain boundaries. It also simplified onboarding and debugging, since each layer had a specific responsibility.

Search functionality:
13) In addition to structured data, we also needed high-performance search functionality. For that, we integrated Apache Solr, which we accessed through a custom-built Solr client library. This allowed us to perform full-text search, faceted filtering, and dynamic sorting — features that would be inefficient in a traditional relational database.

So this is all about the overview of architecture of LI project

legacy start → architectural shift → frontend → business layer → search → summary

The LegalIntelligence project began in 2008, and when I joined the team, it was built using .NET Remoting for backend communication and ASPX pages for the UI, running on .NET Framework 2.0. That was a typical enterprise stack at the time.

As the system scaled and became more complex, we needed better modularity, scalability, and maintainability. Over the next few years, we evolved the architecture to adopt a Service-Oriented Architecture (SOA). We used WCF as the core framework, designing each service as an independent component hosted via Windows Services and exposed through WCF endpoints. This gave us loose coupling and allowed us to scale or update individual services without disrupting the entire system.

The frontend was migrated to ASP.NET MVC for better separation of concerns and a cleaner UI architecture. We added a service proxy layer between the UI and the backend, which communicated with a self-hosted OWIN-based Web API. This abstraction helped keep our business logic clean, testable, and resilient to API changes.

The business layer, deployed on the application server, implemented all domain logic and connected to the database using Entity Framework, applying Repository and Unit of Work patterns. This ensured clean separation of concerns, simplified testing, and improved maintainability.

For high-performance search, we integrated Apache Solr using a custom client library, enabling full-text search, faceted filtering, and dynamic sorting — which wouldn’t have been efficient using only relational queries.

Overall, this architectural evolution enabled us to scale horizontally, enforce domain boundaries, and keep the system flexible and maintainable over a 15+ year lifecycle — which was key to supporting continuous feature development in a complex legal domain.
