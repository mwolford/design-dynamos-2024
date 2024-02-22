# Send Patient Vital Data Snapshot

## Status

- Proposed: 2/19/2024
- Approved: 2/21/2024

## Participants

- Mike Wolford
- Megin Mathew
- Pete Pallo
- Ryan Hertzog

## Context

- MonitorMe system provides functionality to allow Medical Professionals to send patient snapshots to the Cloud Hosts 
- The snapshot will contain the complete data for a single patient from the Patient Vitals History.
- MyMedicalData provides a patient vitals data snapshot upload functionality via HTTPS API.
- MonitorMe Patient Vitals History is a rolling 24 hours of data.
- MonitorMe has a real time monitoring screen that refreshes every 5 seconds.

## Decision

- The MonitorMe monitoring screen will provide functionality for medical professionals to transmit a snapshot of a patient’s vital signs to MyMedicalData.
- The snapshot process will be Asynchronous so that the monitoring screen will not be held up from refreshing during the shopshot upload process.
- A Kafka topic will be used to manage the event lifecycle.
- The MonitorMe Event Choreography app will have a Patient Vitals Data Snapshot Upload Service to process the snapshot upload event.
- The Patient Vitals Data Snapshot Upload Service will include its own MongoDB storage so that the snapshot is saved in the event of a failure in calling MyMedicalData.
- Retry logic will be put in place to ensure MyMedicalData receives the patient vitals snapshot data.
- The MonitorMe call to MyMedicalData  API call will be set to timeout after a set timeframe.

## Consequences

- Monitoring should be put in place to have insight to if MyMedicalData is having problems.

## Supporting Information

- [Sequence Diagram](../diagrams/send-patient-vitals-sequence-diagram.md)
