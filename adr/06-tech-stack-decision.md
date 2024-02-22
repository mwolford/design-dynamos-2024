# Tech Stack for MonitorMe

## Status

  - Proposed: 2/16/2024
  - Approved: 2/20/2024
  
## Participants

  - Brandon Moriarity
  - Mike Wolford
  - Megin Mathew
  - Pete Pallo
  - Ryan Hertzog

## Context

- The MonitorMe system is a monitoring solution that collects and analyzes data from health IoT devices.
- The system needs to be deployed on-premise.
- The project requires a robust, responsive, reliable, and scalable tech stack. 
- The development team is familiar with .NET Core, but there would be a learning curve with Node.js and Docker on-prem deployments.
- Data needs to be stored in a database which supports diverse data types/structures with the ability to handle high traffic loads and scale easily.
- UI needs to be highly responsive, user friendly, and flexible.
- Event streaming needs to provide real-time streaming and processing of data, high availability, and fault tolerance.
- Application is built using microservices architecture.
- Application needs to handle high volumes of traffic with expected response times of 1 second or less.
- The project team will be using CI/CD for deployments.
- The BFF service layer needs to send alerts and vital signs to be displayed on a UI in near real-time.
- Single sign-on needs to be configured for the logging into the MonitorMe app and to secure the communication between our APIs, we need to use token-based authentication.

## Decision

- Database: MongoDB
- Services: .NET Core
- Event Streaming: Apache Kafka
- BFF ServiceLayer: .NET Core (preferred due to team’s familiarity, although Node.js is an alternative)
- UI: React
- Deployment: Docker, Nginx, Node.js
- Server to Client Communication: SignalR
- Authentication: PingFederate

## Consequences

  - Positive outcomes:
    - Utilizing familiar technologies (.NET Core, MongoDB) can lead to increased development speed and fewer bugs.
    - MongoDB's flexible document model allows virtually any data structure to be stored, which can accommodate diverse data types and promote faster development.
    - MongoDB's horizontal scaling capability can handle large amounts of data and high traffic loads.
    - Apache Kafka provides real-time streaming and processing of data, which can improve the responsiveness and performance of the application.
    - Apache Kafka's distributed architecture ensures high availability and fault tolerance.
    - React is flexible and can be applied to various situations, making it easy to modify its behavior to meet your requirements.
    - React's component-based approach promotes reusability and maintainability.
    - React's virtual DOM ensures quick rendering of intricate user interfaces while consuming less memory.
    - React is SEO friendly, which can help improve the visibility of the web application.
    - With SignalR, the UI will be able to display alerts and patient vital signs in near real-time, providing real-time updates.
    - By pushing updates to the client as they become available, we eliminate the need for the client to continuously poll the server for new data, leading to a reduced server Load.
    - SignalR applications can scale out to thousands of clients using built-in or third-party scale-out providers, ensuring scalability.
    - With microservices architecture, Docker allows each service to be packaged into a separate container, ensuring isolation and reducing conflicts between services.
    - With continuous deployment and integration, Docker provides significant advantages. It can package your application and its dependencies into a single object, ensuring consistency across multiple environments, making it ideal for continuous deployment and integration.
    - To handle high traffic, Nginx is really beneficial. As a reverse proxy, it can distribute network traffic to multiple servers to balance the load and ensure high availability.
    - PingFederate enables Single Sign-On for the MonitorMe app, allowing users to access multiple applications with one set of credentials.
    - PingFederate helps secures API communication via token-based authentication, generating unique encrypted tokens for secure access.
  - Impacts to other systems: 
    - The chosen tech stack should integrate well with existing systems.
  - Negative outcomes: 
     - There may be a learning curve with Kafka, Docker on-prem deployments, and potentially with Node.js.

- **Supporting Documentation**
  - Diagrams: [MonitorMe Design](https://s.icepanel.io/g3InyI8xvmzngL/vNwH)
  - Alternate approaches explored: Node.js was considered for the BFF ServiceLayer, but .NET Core was chosen due to the team's familiarity.
