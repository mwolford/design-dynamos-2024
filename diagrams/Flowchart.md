# Flow Chart

## Summary

### MonitorMe Software

The MonitorMe software is a comprehensive patient monitoring system that consists of two main components: an Event Choreography System and the MonitorMe Application.

#### Event Choreography System

This system is responsible for managing the event stream from patient monitoring devices. It performs the following functions:

- Receives vitals from patient monitoring devices and forwards them to the MonitorMe app.
- Generates alerts based on predefined thresholds.
- Sends these alerts to both the MonitorMe app and the StayHealthy mobile app.

#### MonitorMe Application

The MonitorMe app is a robust application that provides a range of functionalities:

- Displays patient vital signs in near real-time.
- Provides access to patient history for the last 24 hours.
- Shows critical alerts related to a patient's vitals.
- Allows uploading of filtered patient vital snapshots to the MyMedicalData application.
- Includes an admin screen for managing devices, patients, nurses, and nurse stations.

This flowchart is designed to provide a clear understanding of the different workflows within the MonitorMe software. It illustrates how the software effectively manages and communicates vital patient data, ensuring timely and accurate patient care.


## Diagram

```mermaid
flowchart LR
    MedicalProfessional[Medical Professional] --login--> MonitorMe(MonitorMe App)
    style MonitorMe fill:#f9d79b
    MonitorMe --> Options[Admin Screen]
    style Options fill:#f7b6d2
    Options --> AddNurseStation[Add Nurse Station]
    Options --> AddPatient[Add Patient]
    Options --> AddDevice[Add Device]
    Options --> AddNurse[Add Nurse]
    AddNurseStation --> AssociateNurse[Associate a Nurse with a Nurse Station]
    AddNurseStation --> AssociatePatients[Associate a Patient with a Nurse Station]
    AssociatePatients --> CheckWorkstationLimit[Check if Workstation Limit 20 Reached]
    CheckWorkstationLimit --> |"Yes"| WorkstationLimitReached[Cannot Add More Patients to Workstation]
    CheckWorkstationLimit --> |"No"| AssociateDevices[Associate devices with a patient]
    AddPatient --> InputPatientDetails[Input Patient Details]
    InputPatientDetails --> CheckPatientLimit[Check if Patient Limit 500 Reached]
    CheckPatientLimit --> |"Yes"| PatientLimitReached[Cannot Add More Patients]
    CheckPatientLimit --> |"No"| SavePatientDetails[Save Patient Details]
    AddDevice --> InputDeviceDetails[Input Device Details]
    InputDeviceDetails --> SaveDeviceDetails[Save Device Details]
    AddNurse --> InputNurseDetails[Input Nurse Details]
    InputNurseDetails --> SaveNurseDetails[Save Nurse Details]
    MonitorMe --> NurseView[Nurse View]
    style NurseView fill:#aed6f1
    NurseView --> ViewPatientVitals[View Patient Vitals]
    ViewPatientVitals --> RotateVitals[Rotate Between Patients Every 5 Seconds]
    NurseView --> ReceiveAlerts[Receive Critical Alerts]
    NurseView --> UploadVitals[Upload Patient Vital Snapshots]
    UploadVitals --> EventChoreographyLayer[Event Choreography Layer]
    style EventChoreographyLayer fill:#82e0aa
    EventChoreographyLayer --> MyMedicalData[MyMedicalData]
    NurseView --> ViewVitalsHistory[View Patient Vitals History]
    IoTDevices[IoT Devices] --> SendVitals[Send Vitals to Event Choreography Layer]
    style IoTDevices fill:#f5b7b1
    SendVitals --> EventChoreographyLayer
    EventChoreographyLayer --> MonitorMe
    EventChoreographyLayer --> GenerateAlerts[Generate Critical Alerts]
    GenerateAlerts --> MonitorMe
    GenerateAlerts --> StayHealthyApp[StayHealthy Mobile App]
    MonitorMe --> SaveVitalsFor24Hours[Save Patient Vitals for 24 Hours]

```

## Supporting Documents

Icepanel C4: [MonitorMe Software Design](https://s.icepanel.io/g3InyI8xvmzngL/Z3NK)

