Angular Focused on Fundamentals:
Components, Services, Modules
Data Binding
Lifecycle Hooks
Routing
Dependency Injection
RxJS basics (Observables, subscribe)
Forms (Template-driven vs Reactive)

Could you explain what SOLID principles are and how they apply in Angular? 

SOLID principles are the five principles of object-oriented class design. These are the set of rules and best practices to follow while designing the class structure. 

These principles are also very relevant in Angular development, especially since Angular encourages component-based architecture and dependency injection

S in SOLID stands for single responsibility, which say that a class or component should take part in single responsibility. 
In other words, there should be only one reason to change a particular class.
In Angular, this means separating concerns. For example, if I have a component that handles UI and also fetches data, that violates SRP. Instead, I’d move the data-fetching logic into a service. That way, the component just handles the view, and the service handles business logic or HTTP calls.

O in solid stands for the Open Close Principle, which say that the classes should be open for enhancements but closed for modifications.
In Angular, this often applies to services or classes that we might need to extend without modifying existing code.
For example, if I have a base logging service, I can extend it in another class to add custom behavior like sending logs to a server—without altering the original class. Angular’s dependency injection system supports this well by allowing us to provide different implementations via interfaces or tokens.

L in solid stands for the "lik-so-vis" substitution principle, which say that derived classes should be substitutable for their base classes.
In Angular, this might come up when creating components or services that extend other classes. For instance, if I have a base NotificationService and then a subclass EmailNotificationService, the subclass should behave in a way that doesn’t break expectations when used in place of the base class—like in a component that just expects some sort of notification service.


D in solid stands for dependency inversion which says classes should not be instantiating other classes, which they require to achieve their functionality. 
Instead, there should be a container class, which should create objects of all the classes and inject whatever dependencies are required in whichever classes by itself.
In Angular we do not directly 