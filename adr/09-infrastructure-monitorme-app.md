# MonitorMe App Infrastructure

## Status

- Proposed 2/20/2024
- Approved 2/21/2024

## Participants

- Mike Wolford
- Megin Mathew
- Brandon Moriarty
- Ryan Hertzog
- Pete Pallo

## Context

- MonitorMe App contains multiple components
   - REACT Web UI
   - .NET Core API's for the backend for frontend (bff)
   - nodeJS Web hosting
   - SignalR websockets
- MonitorMe needs refreshed data within 1 second of vital data updates.

## Decision

- Three docker image will created to allow isolation of resourcing for aspects that need more.
- One container for the BFF services and SignalR.
- One container for REACT Web UI, signalR and nodeJS.
- One container for the Admin screen services which includes device, nurse, patient and nurse station setup.
- We will use 2 servers to host the image for load balancing.
- We will set up two isolated virtual machines, with each instance setup as hot-hot configuration.
- F5 will be used to balance traffic between node 1 and node 2 in a balanced 50/50 configuration.
- Each virtual machine will need 4 CPU with 32 cores and 32GB of Memory running Linux OS.
- We will use SingalR to be our websocket connection to push new vital data to each nurse station UI.

## Consequences

- We feel it is acceptable for the resource to scale as a whole rather than independently, considering that REACT is a browser-based solution and scaling will be necessary for the BFF.
- Datacenter is built for all proper fault tolerance needs such as power backup, power surge prevention

## References
