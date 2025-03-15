# Basics of distributed systems

## What Is Distributed Systems?
in distributed systems, software is divided into independent and scalable components. These components and services collaborate to function as an integrated system. Typically, they are networked and communicate with each other to provide a unified service

### Features of distributed systems
- **Transparency** – Users should not be aware that the system consists of multiple nodes. Transparency applies to access, location, migration, concurrency, and failure handling.

- **Scalability** – The system should efficiently accommodate an increasing number of nodes without performance degradation.

- **Fault Tolerance** – The system must continue functioning even if some nodes fail, ensuring high availability and reliability.

- **Concurrency** – Multiple processes or users should be able to interact with the system simultaneously without conflicts.

- **Coordination** – Nodes must synchronize and manage data and processing efficiently to maintain system integrity.

- **Security** – Authentication, authorization, and data protection mechanisms must be in place to prevent attacks and ensure secure communication.

### Common Architectures in Distributed Systems

- **Client-Server Architecture** – Clients send requests to a central server, which processes them and returns responses.

- **Peer-to-Peer (P2P) Architecture** – Each node acts as both a client and a server, sharing resources directly without a central authority.

- **Microservices Architecture** – The system is divided into independent services, each handling a specific function, communicating via APIs.

- **Event-Driven Architecture** – Components communicate asynchronously by sending and responding to events rather than direct calls.

- **Service-Oriented Architecture (SOA)** – Services interact over a network using standardized protocols, promoting reusability and interoperability.

- **Serverless Architecture** – Applications are executed in a cloud-based environment where resources are allocated dynamically, reducing infrastructure management overhead.

## Monolithic vs. Distributed Systems Comparison

| Aspect                | Monolithic System | Distributed System |
|----------------------|------------------|-------------------|
| **Architecture**    | Single, unified application | Multiple independent services |
| **Scalability**     | Limited; scaling requires duplicating the whole system | High; can scale individual components separately |
| **Deployment**      | Easier, as everything is in one place | More complex, requiring orchestration tools (e.g., Kubernetes) |
| **Development Speed** | Faster for small projects | Slower due to complexity and inter-service communication |
| **Maintenance**     | Can become difficult as the codebase grows | Easier to maintain individual components |
| **Fault Tolerance** | A failure in one part may crash the entire system | More resilient, failures in one service don’t affect others (if properly designed) |
| **Performance**     | Can be efficient for small applications | Better suited for large-scale applications with high traffic |
| **Flexibility**     | Less flexible; changing one part affects the whole system | More flexible; services can be modified independently |
| **Technology Stack** | Typically uses a single technology stack | Allows different services to use different technologies |
| **Security**        | Easier to secure since everything is in one place | More complex security due to multiple entry points |
| **Cost**           | Lower initial cost but higher long-term maintenance cost | Higher initial investment but more cost-effective at scale |
| **Time to Market**  | Faster for simple applications | Slower due to the need for managing multiple components |
| **Examples**       | Traditional enterprise applications, CMS, ERP | Cloud-native applications, e-commerce, microservices-based platforms |



