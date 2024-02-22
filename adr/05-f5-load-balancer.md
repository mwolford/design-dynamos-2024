# F5 Load Balancer

## Status

- Proposed: 2/20/2024
- Approved: 2/21/2024

## Participants

- Mike Wolford
- Megin Mathew
- Ryan Hertzog
- Pete Pallo

## Context

- MonitorMe needs to be durable and online as much as possible.
- MonitorMe needs to scale due to load.

## Decision

- Use F5 layer 4 transport routing to direct traffic to nodes for hot - hot implementation.
- Use F5 layer 7 application routing to secure our environment.

## Consequences

- Ensuring that systems are protected based on the application request needs.

## Supporting Information
