# Event Choreography App Infrastructure

## Status

- Proposed: 2/20/2024
- Approved 2/21/2024

## Participants

- Mike Wolford
- Megin Mathew
- Brandon Moriarty
- Ryan Hertzog
- Pete Pallo

## Context

- MonitorMe is using Event Driven Architecture using Kafka
- MonitorMe is using Micro-service architecture using .NET Core services
- Independent devices will send patient vital's data per vital, and the rate of events depends on each device.
  - Heart rate: every 500ms
  - Blood pressure: every hour
  - Oxygen level: every 5 seconds
  - Blood sugar: every 2 minutes
  - Respiration: every second
  - ECG: every second
  - Body temperature: every 5 minutes
  - Sleep status: every 2 minutes

## Decision

- We will have 2 instances of Kafka for redundancy running in their own container and host Linux Os.
- We will have a container per micro-service (8), running on 2 instances of Linux OS hosts.
- Each containers will be allocated the proper resources based on the load of each vital.
- We will use F5 layer 4 to route traffic to Kafka.
- We will use F5 layer 4 to balance routing of microservices.

## Consequences

- Microservices will balance 50/50 load for performance and redundancy.
- Kafka will be set up with Active/Passive.

## References

- [F5 Load Balancing use cases](https://www.f5.com/solutions/use-cases/load-balancing-your-applications)

