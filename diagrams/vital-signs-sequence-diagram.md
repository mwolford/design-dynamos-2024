# Vitals Sequence Diagram

This diagram shows the flow of vital data as it leaves the device and how it's used throughout the MonitorMe System.  The flow is for a single Vital as the pattern will be the same for all other services.

``` mermaid

sequenceDiagram

    actor p as Patient
    participant d as Vital Device
    box LightGreen MonitorMe Vitals Event Choreography App
        participant k as Kafka
        participant ms as Vital Service
        participant msDb as Vital Database
    end
    participant sh as StayHealthy
    box LightBlue MonitorMe Application
        participant bff as Backend for Frontend
        participant vdb as Patient Vitals History Database
        participant ns as Nurse Station Setup Service
        participant nsdb as Nurse Stations Database
        participant sgr as SignalR
        participant ui as UI
    end
    p --> d: Read Vital
    d ->> k: New Vital Event Data
    k -->> ms: New Event
    activate ms
        ms ->>+ msDb: Save Raw Event
        msDb -->>- ms: Save Complete
        ms ->> bff: Send Raw Vital Data
    activate bff
        ms ->> ms: Determine if Alert needed
        opt Alert Needed
            ms ->> sh: Alert
        end
        bff ->>+ vdb: Save Vital data
        vdb -->>- bff: Save Complete
        bff -->> ms: Received Vital Data
        deactivate ms
        bff ->> ns: Get Nurse Station for Patient
        activate ns
            ns ->>+ nsdb: Get Nurse Station for Patient
            nsdb -->>- ns: Associated Nurse Station
        ns -->> bff: Associated Nurse Station
        deactivate ns
        bff -->>+ sgr: Push New Vital to Nurse Station
    deactivate bff
    sgr ->>- ui: New Vital
```