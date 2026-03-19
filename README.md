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
