# ceg3006_project

Brief Description
PPAS-P (Predictive Phantom Pedestrian Alert System) is a Vehicle-to-Pedestrian (V2P) safety system designed to address pedestrian collision risks caused by visual occlusions in urban environments. These occlusions commonly occur due to buses, parked vehicles, roadside structures, or building corners, which prevent drivers from detecting pedestrians using conventional line-of-sight sensors.
The system leverages direct V2P communication using technologies such as C-V2X (PC5 sidelink mode) or IEEE 802.11p (DSRC). A pedestrian’s smartphone or wearable device broadcasts periodic safety beacons containing position, velocity, heading, and inferred crossing intent. These beacons are received by the vehicle’s On-Board Unit (OBU), enabling detection even when the pedestrian is physically hidden from view.
Upon receiving the beacon, the vehicle performs edge-based risk estimation by projecting both pedestrian and vehicle trajectories over a short prediction horizon (2–3 seconds). The system calculates Time-To-Collision (TTC) and Closest Point of Approach (CPA) to determine risk severity. Alerts are issued in tiered levels (advisory, urgent, critical) depending on predicted collision likelihood. All safety-critical processing occurs locally within the vehicle to ensure low latency and independence from cloud infrastructure.
PPAS-P enhances urban road safety by combining vehicular networking with predictive modeling, specifically targeting occlusion scenarios that traditional ADAS systems struggle to handle.

Literature Review & Differentiation

Current pedestrian safety systems generally fall into three categories.
First, vision-based Advanced Driver Assistance Systems (ADAS) rely on cameras, radar, or LiDAR to detect pedestrians. While effective in open conditions, these systems require direct line-of-sight and experience significant performance degradation under occlusion, poor lighting, or adverse weather conditions. As a result, sudden “emerging pedestrian” scenarios remain a persistent risk.
Second, infrastructure-assisted smart intersection systems deploy roadside units (RSUs) equipped with sensors to monitor pedestrian crossings. These systems improve detection reliability but are location-specific and costly to deploy at scale, limiting their practicality in widespread urban environments.
Third, existing V2P proximity warning systems using technologies such as C-V2X and IEEE 802.11p primarily focus on broadcasting presence information. However, many implementations rely on simple distance-based alerts without incorporating predictive trajectory analysis, which can lead to either late warnings or excessive false positives.
PPAS-P differentiates itself by integrating direct V2P communication with predictive edge-based risk estimation. Instead of issuing alerts solely based on proximity, the system evaluates TTC, trajectory intersection probability, and confidence levels over a defined prediction horizon. This enables earlier and more precise warnings while reducing unnecessary driver distraction. Additionally, the system avoids dependence on fixed infrastructure and cloud processing, ensuring scalability, lower latency (<100 ms), and improved reliability in safety-critical scenarios.

<img width="869" height="510" alt="image" src="https://github.com/user-attachments/assets/077821ac-89e4-4b67-b09b-d7a7bc2cb63b" />

<img width="866" height="344" alt="image" src="https://github.com/user-attachments/assets/81ca0263-5322-479b-bec5-dc285f0c68c3" />

<img width="906" height="382" alt="image" src="https://github.com/user-attachments/assets/cb26a07e-968a-4946-a3ab-98b499ea2a4b" />

<img width="883" height="401" alt="image" src="https://github.com/user-attachments/assets/0ce1e1a0-0ec2-4835-92a2-ce0911d2cf8d" />

<img width="864" height="330" alt="image" src="https://github.com/user-attachments/assets/785ce32e-1591-4a82-b0b3-0f70fb58bcf3" />

<img width="891" height="296" alt="image" src="https://github.com/user-attachments/assets/f405ba31-205d-416f-91a0-c5dd9ccd2eb7" />

<img width="879" height="380" alt="image" src="https://github.com/user-attachments/assets/b4557db6-85c7-483c-85fa-e7e3dced1a3c" />

SYSTEM ARCHITECTURE

<img width="679" height="229" alt="image" src="https://github.com/user-attachments/assets/8a754135-cea2-4386-95e6-a36d62513716" />
The PPAS-P system consists of four main subsystems: Pedestrian Devices, V2P Communication, Vehicle Edge OBU, and Driver HMI. The pedestrian device collects motion and intent data and broadcasts periodic safety beacons via direct V2P communication (C-V2X or IEEE 802.11p). The vehicle’s OBU receives these beacons, performs edge-based risk estimation, and determines collision likelihood. Based on the predicted risk, the system issues tiered alerts to the driver through the HMI.

<img width="704" height="268" alt="image" src="https://github.com/user-attachments/assets/5933265a-5f97-444f-b274-3261852a7975" />
The Vehicle Edge OBU processes incoming pedestrian beacons together with vehicle state data to estimate collision risk. After validating and synchronising the data, the system projects pedestrian and vehicle trajectories over a short time horizon. It then computes risk metrics such as Time-To-Collision (TTC) and Closest Point of Approach (CPA) to classify threat levels. The alert manager translates this risk into tiered warnings delivered to the driver or ADAS system.

SYSTEM FLOW CHARTS & PSEUDO CODE

<img width="525" height="1135" alt="image" src="https://github.com/user-attachments/assets/1423d75d-e5f7-47ba-960b-4476582e56a1" />
<img width="829" height="934" alt="image" src="https://github.com/user-attachments/assets/ffbd924a-8461-4ced-96d4-803af5472cda" />
This pseudocode describes how the vehicle processes incoming pedestrian beacons to assess collision risk. It extracts both pedestrian and vehicle states, predicts their future trajectories, and computes safety metrics such as Time-to-Collision (TTC) and Closest Point of Approach (CPA). Based on these values, the system classifies the risk level and determines whether to trigger an emergency alert, a warning, or no alert. This ensures timely driver notification in potentially dangerous situations.

<img width="456" height="1146" alt="image" src="https://github.com/user-attachments/assets/72f6592a-f18f-4f12-9cfe-22851e332c35" />
<img width="879" height="844" alt="image" src="https://github.com/user-attachments/assets/98a05c63-4d63-4c9e-9c85-d3a99af49fe5" />
This describes the operation of the pedestrian-side system that continuously monitors movement. When movement is detected, it collects key data such as position, speed, heading, and timestamp. These parameters are then packaged into a safety beacon message. The beacon is transmitted via C-V2X to nearby vehicles to support real-time collision risk assessment.

<img width="697" height="1102" alt="image" src="https://github.com/user-attachments/assets/b0d7a769-b003-4fb6-8f9a-2391bc560f6d" />
<img width="792" height="959" alt="image" src="https://github.com/user-attachments/assets/9a93b636-82f8-46ee-a3ec-eb55de0fa1c1" />
This shows how the vehicle processes incoming pedestrian beacons to ensure data reliability. It first verifies the beacon format and timestamp, discarding invalid or outdated messages. Once validated, the system extracts key pedestrian information such as position, speed, and heading. This data is then used to update the pedestrian tracking model. Finally, the processed information is forwarded to the risk assessment module for further analysis.

<img width="919" height="1290" alt="image" src="https://github.com/user-attachments/assets/7d4f6498-0ef0-45c7-a6ef-3045cff4cde1" />
<img width="1031" height="1058" alt="image" src="https://github.com/user-attachments/assets/78168636-cc60-448d-88f7-091a2f92ae95" />
This code outlines the decision-making logic used to classify collision risk and trigger appropriate alerts. It compares TTC values against predefined thresholds to decide between emergency, warning, or no alert actions. After determining the alert level, the system records the relevant data for future reference and system evaluation.

Figure 7 shows how the system handles missing beacons by tracking packet loss and adjusting confidence levels.
<img width="978" height="1313" alt="image" src="https://github.com/user-attachments/assets/16532299-143a-4d3e-92c9-7e6c3288c5ce" />

<img width="986" height="965" alt="image" src="https://github.com/user-attachments/assets/0810132e-71e4-4dc5-baad-ec375305b306" />
This pseudocode outlines the process of detecting communication loss and adjusting system behavior accordingly. It resets tracking when data is received but increases a missed counter when signals are absent. Once a threshold is crossed, the system degrades its confidence level, marks uncertainty, and limits alert generation to prevent false warnings.

Figure 8 shows how the system converts risk levels into appropriate driver alerts, ranging from no alert to visual warnings and emergency audio alerts.
<img width="688" height="1112" alt="image" src="https://github.com/user-attachments/assets/9b03da25-3b99-4f51-a464-0de507bc8581" />

<img width="1034" height="989" alt="image" src="https://github.com/user-attachments/assets/3a78b530-9825-4bf4-ada6-35882d3a2f98" />
This defines how the system responds to different alert levels generated by the risk module. It uses a switch-case structure to map each risk level to a specific driver notification. For a low risk, the system displays a safe status with no warning. For medium risk, it provides a visual warning on the dashboard, while for high risk, it triggers both a visual warning and an audio alarm to indicate immediate danger.

USE CASE IN REAL-WORLD SCENARIO
In a busy urban street, a pedestrian begins crossing the road from between two parked cars, making them completely hidden from an approaching driver. The pedestrian’s smartphone continuously sends out its location, speed, and direction using a C-V2X communication system. These messages are transmitted at short intervals, allowing nearby vehicles to stay updated on the pedestrian’s movement in real time.

As a vehicle approaches the area, its onboard system receives this information and combines it with its own speed and direction. The system then predicts where both the pedestrian and the vehicle will be in the next few seconds. Even though the pedestrian cannot be seen by the driver or detected by cameras due to the obstruction, the system can still recognise a potential collision.

It does this by calculating how soon the vehicle and pedestrian might meet and how close they will get to each other. If the situation is considered dangerous, the system immediately sends a warning to the driver through visual or audio alerts inside the vehicle. This early warning allows the driver to slow down or stop in time, preventing an accident and improving safety in situations where visibility is limited.
