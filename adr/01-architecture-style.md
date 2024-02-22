# Architecture Style

## Status

  - Proposed: 2/15/2024
  - Accepted: 2/16/2024

## Participants

  - Mike Wolford
  - Ryan Hertzog
  - Pete Pallo
  - Brandon Moriarty

## Context

  - In the health care industry responding to changes in vital signs is key to providing the best care and life saving treatment.
  - Reporting of each vital sign needs to be as quick as possible.
  - There are up to 8 patient monitoring devices on up to 500 patients for vital signs producing data at different intervals.
  - Each vital sign report for a patient needs to work independently of other vital sign reports.
  - Strengths of a microservices architecture include fault isolation, data isolation, and scalability which will help meet the needs of the patient monitoring solution.
  - Strengths of event driven architecture include decoupling and independence, scalability, and real-time processing.
 
## Decision

  - Use a blend of event-driven architecture for device data ingestion along with microservices throughout the system to provide a solution that is highly responsive, fault tolerant, and maintains data integrity for each vital sign.

## Consequences

  - Combining microservices with event-driven architecture will allow the system to handle a large number of events concurrently, ensuring high throughput and responsiveness.
  - The components for each vital sign will be decoupled from each other, meaning that changes to one component will not directly effect others.
  - The system should be able to recover independently from failures. If one service fails, all others should be able to continue processing.
  - Testing can be more complicated in a solution developed using microservices and event-driven architecture.
  - Debugging the system may be more difficult due to the distributed nature.
  - Systems designed in this way have a tendency to be overengineered or overly complex. This complexity can make design and implementation more challenging.

## Supporting Documentation

  - [Architecture Characteristics](https://github.com/mwolford/design-dynamos-kata-2024/blob/main/adr/supportingDocuments/architecture-characteristics-worksheet.pptx)
  - [Architecture Style](https://github.com/mwolford/design-dynamos-kata-2024/blob/main/adr/supportingDocuments/architecture-styles-worksheet.pptx)
