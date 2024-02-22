# Send Patient Vitals Sequence Diagram

This diagram visualized the flow and interactions for when a Nurse takes action to snapshot a patient data and send to MyMedicalData system.

``` mermaid

sequenceDiagram
    actor mp as  Medical Professional
    participant ui as MonitorMe Patient Nurse Station UI
    participant bff as MonitorMe Backend for frontend
    participant db as MonitorMe Patient Vitals History
    participant topic as Vital Data Snapshot Event Topic
    participant ms as Vital Data Snapshot Service
    participant msdb as Vital Data Snapshots Database
    participant mmd as MyMedicalData

    mp ->> ui: Send Patient Vital Snapshot
    ui ->> bff: Send Patient Vital Snapshot
    activate bff
        bff -) topic: Vital data Snapshot Request Event for Patient
        bff -->> ui: Vital data Snapshot Request captured
    deactivate bff
    topic --) ms: New Vital data Snapshot Event
    activate ms
        ms ->>+ bff: Get Patient data
        bff ->>+ db: Get Patient data
        db -->>- bff: All Patient data
        bff -->>- ms: Patient Vital data Snapshot data
        ms ->>+ msdb: Save Patient Vital data Snapshot data
        msdb -->>- ms: Save complete
        loop Until Success
            ms ->> mmd: Send Vital data Snapshot via HTTPS
        end
        ms ->> ms: Delete Vital data Snapshot            
            
    deactivate ms
    
```