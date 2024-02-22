# System Monitoring

## Status

- Proposed: 2/20/2024
- Approved: 2/20/2024

## Participants

- Mike Wolford
- Pete Pallo
- Brandon Moriarty
- Megin Mathew

## Context

- MonitorMe is a health care system that runs on premise and as a health care system it is important to be proactive with problems to keep the system online.
- MonitorMe is a distributed architecture with internal component dependencies and external system dependencies.

## Decision

- We will use Dynatrace Application Performance Monitoring system to monitor system and application health, enabling proactive support for MonitorMe.
- We will use Dynatrace OneAgent on premise to collect log metrics and send them to Dynatrace running in Azure Cloud.
- We will use Dyantrace ActiveGate Agent on its own host Linux OS.

## Consequences

- OneAgent needs to be included in all code, including .NET and REACT, to gather application logs and metrics.
- OneAgent needs to be installed into the docker containers to gather infrastructure logs and metrics.

## References

- [DynaTrace Docker Container Setup](https://docs.dynatrace.com/docs/setup-and-configuration/setup-on-container-platforms/docker/set-up-dynatrace-oneagent-as-docker-container)
