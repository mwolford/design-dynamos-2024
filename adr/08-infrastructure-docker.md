# Infrastructure - Docker

## Status

- Proposed 2/19/2024
- Approved 2/21/2024

## Participants

- Mike Wolford
- Ryan Hertzog
- Megin Mathew

## Context

- The MonitorME system is a monitoring solution that collects and analyzes data from health IOT devices.
- The system needs to be deployed on-premise to meet specific security and compliance requirements.
- Docker containers provide a lightweight and portable way to package and deploy applications.

## Decision

- We have decided to use Docker images to deploy the MonitorME system on-premise. Docker allows us to encapsulate the application and its dependencies into a single container, ensuring consistency and reproducibility across different environments. By using Docker, we can easily manage and scale the infrastructure, as well as simplify the deployment process.
- We will make multiple containers based on the need of the systems.

## Consequences

Using Docker images for the infrastructure of the MonitorME system brings several benefits:

- **Portability**: Docker containers can be easily moved between different environments, ensuring consistency and reducing deployment issues.
- **Isolation**: Each component of the MonitorME system can run in its own container, providing isolation and minimizing the impact of failures.
- **Scalability**: Docker enables horizontal scaling by allowing multiple instances of the system to run concurrently, providing high availability and performance.
- **Versioning**: Docker images can be versioned, allowing us to roll back to previous versions if needed.
- **Ease of Deployment**: With Docker, the deployment process becomes more streamlined and automated, reducing manual errors and saving time.

However, there are also some considerations and challenges to be aware of:

- **Learning Curve**: Docker has its own set of concepts and commands that team members need to learn and understand.
- **Resource Overhead**: Running applications in containers introduces some resource overhead compared to running them directly on the host machine.
- **Security**: Proper security measures need to be implemented to ensure the integrity and confidentiality of the MonitorME system and its data.

Overall, using Docker images for the infrastructure of the on-premise MonitorME system provides a flexible and scalable solution that meets the specific requirements of the project.
