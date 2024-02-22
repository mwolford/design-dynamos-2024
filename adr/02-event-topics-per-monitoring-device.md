# Event Topics Per Monitoring Device

## Status
  - Approved 2/16/2024
  
## Participants
  - Brandon Moriarity
  - Mike Wolford
  - Megin Mathew
  - Pete Pallo
  - Ryan Hertzog

## Context
  - StayHealthy, Inc. is expanding into the medical monitoring market and will be implementing a new medical patient monitoring system, known as MonitorMe.
  - MonitorMe is intended to be used by hospitals and medical professionals to monitor and alert on patient vital signs using proprietary medical monitoring devices built by StayHealthy, Inc.
  - As this is a new line of business for StayHealthy, Inc. change is expected as they learn more about this new market.
  - Additionally, StayHealthy, Inc. anticipates more vital sign monitoring devices will be added to MonitorMe in the future.
  - The proposed event-driven microservice architecture is designed to be scalable, adaptable, reliable, while ensuring data integrity, responsiveness, and fault tolerance. 

## Decision
  - Create separate event topics for each monitoring device in the Event Choreography application.

## Consequences
  - By using separate event topics per monitoring device the following is accomplished;
    - MonitorMe system can scale to handle the varying data transmittal rates of each device.
    - Failure of any monitoring device or software will not impact the others, allowing for the MonitorMe system to function for other monitoring devices. 
    - Provides efficient event routing to the appropriate microservices, in near real-time, ensuring a responsive system.
    - Ability to ensure accuracy and validity of the transmitted patient data, by each monitoring device, through data isolation, error handling, and data validation within the respective microservice.
    - As StayHealthy, Inc. plans to add more monitoring devices in the future, using separate topics allows for easy integration of new devices.
  - This inherently leads to additional complexity such as managing multiple topics, event streams, data storage, and monitoring and alerting capabilities within the Event Choreography application.
