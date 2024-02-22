# MongoDB Infrastructure

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

- Store a rolling 24 hours of patient vitals in MonitorMe.
- Allow filtering and sorting of patient data in MonitorMe.
- Export snapshots of a patient's data to upload to MyMedialData using MonitorMe.

## Decision

- Install MongoDB on 3 nodes, in a Primary, Second, Tertiary configuration.
- Create a private VNET for the MongoDB Nodes to manage fail over.
- Use 3 virtual machines.
- Use Azure Backup service to export periodic backups to an offsite location in Azure Cloud.

## Consequences

- Ensure proper redundancy to apply MongoDB upgrades and protect against outages.
- Offsite backups will ensure that we have a proper RPO.

## References

- [MongoDB Install Guide](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-community-with-docker/)
