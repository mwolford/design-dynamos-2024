# Microservices

## Status

- Approved: 2/20/24

## Participants

- Mike Wolford
- Brandon Moriarity
- Megin Mathew
- Ryan Hertzog
- Pete Pallo

## Context

- MonitorMe reads data from eight different patient-monitoring equipment vital sign input sources. Each device transmits vital sign readings via an event stream at a different rate.
- The vital sign data needs to get sent to a consolidated monitoring screen (per nurses station) with an average response time of 1 second or less.
- For each vital sign, MonitorMe must record and store the past 24 hours of all vital sign readings. A medical professional can review this history, filtering on time range as well as vital sign.
- In addition to recording raw monitoring data, the MonitorMe software must also analyze each patient’s vital signs and alert a medical professional if it detects an issue (e.g., decrease in oxygen level) or reaches a preset threshold (e.g., temperature has reached 104 degrees F).
- Some trend and threshold analysis is dependent on whether the patient is awake or asleep. For example, if the blood pressure drops, the system should notice that the patient is asleep and adjust its alerts accordingly. The same is true with the respiration rate and heart rate. All of these vital signs are reduced when the patient is asleep, but if awake something might be wrong.
- Medical professionals receive alert push notifications of a potential problem based on raw data analysis to a StayHeathy mobile app on their smart phone as well as the consolidated monitoring screen in each nurses station.
- If any vital sign device (or software) fails, MonitorMe must still function for other vital signs (monitoring, recording, analyzing, and alerting).

## Decision

- The MonitorMe system will implement discrete microservices to encapsulate all functionality as it pertains to each service boundary.
- Each vital sign microservice will be responsible for monitoring, recording, analyzing, and alerting based on their own thresholds.
- The blood pressure, respiration, and heart rate service will subscribe to the sleep status event topic so they can take that data into account when doing their analysis.
- In addition to the vital sign microservices, MonitorMe will have microservices for device registry, nurse registry, patient registry, nurse station setup, and patient vitals history.
- A backend for frontend (BFF) pattern will be leveraged to separate the backend microservices from the MonitorMe web UI and StayHealthy mobile application frontend.

## Consequences

- Encapsulating all capabilities of each vital sign into their own microservice decouples them from each other. In the event that one of them fails the others will continue to function independently of each other.
- Leveraging a BFF allows us to fine-tune the behavior and performance of each backend to best match the needs of the frontend environment, without worrying about affecting other frontend experiences.
