# Architecture Cheat Sheet

## Fundamentals of Data Engineering

### Architecture

#### Princicples

1. Choose Common Components Wisely
2. Plan for Failure

> Everything fails, all the time.

3. Architect for Scalability

* Scale up to handle significant amounts of data.
* Scale to zero to shut down a system completely when not in use.
* However note, that overcomplicated scaling strategies can result in overcomplicated systems and high costs.

4. Architecture is Leadership

> Strong leadership skills combined with high technical competence are rare and extremely valuable.

> Note that leadership does not imply a command-and-control approach to technology.

5. Always be Architecting

> We add that modern architecture should not be command-and-control or waterfall but collaborative and agile.

6. Build Loosely Coupled Systems

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

> When the architecture of the system is designed to enable teams to test, deploy, and change systems without dependencies on other teams, teams require little communication to get work done. In other words, both the architecture and the teams are loosely coupled.

For software architecture, a loosely coupled system has the following properties:

* Systems are broken into many small components.
* These systems interface with other services through abstraction layers, such as a messaging bus or an API. These abstraction layers hide and protect internal details of the service, such as a database backend or internal classes and method calls.
* As a consequence of property 2, internal changes to a system component don’t require changes in other parts. Details of code updates are hidden behind stable APIs. Each piece can evolve and improve separately.
* As a consequence of property 3, there is no waterfall, global release cycle for the whole system. Instead, each component is updated separately as changes and improvements are made.

Notice that we are talking about technical systems. We need to think bigger. Let’s translate these technical characteristics into organizational characteristics:

* Many small teams engineer a large, complex system. Each team is tasked with engineering, maintaining, and improving some system components.
* hese teams publish the abstract details of their components to other teams via API definitions, message schemas, etc. Teams need not concern themselves with other teams’ components; they simply use the published API or message specifications to call these components. They iterate their part to improve their performance and capabilities over time. They might also publish new capabilities as they are added or request new stuff from other teams. Again, the latter happens without teams needing to worry about the internal technical details of the requested features. Teams work together through loosely coupled communication.
* As a consequence of characteristic 2, each team can rapidly evolve and improve its component independently of the work of other teams.
* Specifically, characteristic 3 implies that teams can release updates to their components with minimal downtime. Teams release continuously during regular working hours to make code changes and test them.

7. Make Reversible Decisions

> One of an architect’s most important tasks is to remove architecture by finding ways to eliminate irreversibility in software designs.

8. Prioritize Security

> In the corporate world today, a command-and-control approach to security is quite common, wherein security and networking teams manage perimeters and general security practices. The cloud pushes this responsibility out to engineers who are not explicitly in security roles. Because of this responsibility, in conjunction with more general erosion of the hard security perimeter, all data engineers should consider themselves security engineers.

9. Embrace FinOps

> FinOps is an evolving cloud financial management discipline and cultural practice that enables organizations to get maximum business value by helping engineering, finance, technology, and business teams to collaborate on data-driven spending decisions.



## Cloud Provider Frameworks

### AWS Well Architected Guide

https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html

### GCE 5 Principles for Cloud-Native Architecture

https://cloud.google.com/blog/products/application-development/5-principles-for-cloud-native-architecture-what-it-is-and-how-to-master-it?hl=en
