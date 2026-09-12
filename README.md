# DCPS_group5
# Model-Based Design & Verification of an Autonomous Robotaxi Highway Merge System

> **Cyber-Physical Systems | Autonomous Driving | SysML | UPPAAL | Formal Verification**

## 📌 Project Overview

This project focuses on the **model-based design and formal verification of an autonomous electric robotaxi highway merge system**.

A highway merge is a safety-critical driving scenario that requires continuous coordination among perception, prediction, planning, and vehicle control functions. The system was designed using **SysML** and subsequently translated into **UPPAAL Timed Automata** to verify safety, reachability, and timing-related requirements.

The project covers the complete engineering process from **requirements analysis and system modeling to formal verification**.

- **Institution:** University of Southern Denmark (SDU)
- **Course:** Design of Reliable Cyber-Physical Systems
- **Project Type:** Team Project
- **Tools:** Visual Paradigm, UPPAAL
- **Domain:** Autonomous Driving / Cyber-Physical Systems / Model-Based Systems Engineering


## 🎯 Project Objective

The objective of this project was to design and verify a reliable autonomous highway merge system capable of:

- Monitoring surrounding vehicles
- Predicting vehicle positions and relative velocities
- Evaluating safe traffic gaps
- Planning a safe merge trajectory
- Coordinating steering, braking, and propulsion
- Handling unsafe gaps and emergency situations

The overall development process was:

```text
Requirements Analysis
        ↓
SysML System Modeling
        ↓
Behavior & State Machine Design
        ↓
UPPAAL Timed Automata Modeling
        ↓
Formal Verification
```


## 🚗 Highway Merge Scenario

When the autonomous robotaxi enters a highway on-ramp, the system performs the following sequence:

1. Detect and monitor surrounding vehicles
2. Predict their positions and relative velocities
3. Evaluate available traffic gaps
4. Identify a safe gap for merging
5. Generate a merge trajectory and speed profile
6. Execute steering, braking, and propulsion commands
7. Continuously monitor safety conditions during the maneuver
8. Abort or initiate emergency braking if unsafe conditions occur
9. Complete the merge when all safety conditions are satisfied


## 📋 System Requirements

The highway merge scenario was defined through explicit functional and safety requirements.

| ID | Requirement |
|---|---|
| **MERGE-001** | Continuously track vehicles in the adjacent highway lane within a 150 m range |
| **MERGE-002** | Calculate relative velocities and predicted positions over a 10-second horizon |
| **MERGE-003** | Identify a minimum safe gap of at least 4 seconds |
| **MERGE-004** | Compute a smooth acceleration profile for safe merging |
| **MERGE-005** | Initiate a gap request if no acceptable gap is found before the final 50 m of the merge lane |
| **MERGE-006** | Abort the merge and select another gap if the target gap becomes unsafe |
| **MERGE-007** | Apply maximum braking when an imminent collision is detected |


## 🏗 System Architecture

The autonomous robotaxi was modeled as a Cyber-Physical System consisting of several interacting subsystems:

- **Sensor System**
- **AI Control Unit**
- **Brake System**
- **Steering System**
- **Powertrain System**
- **Cloud System**
- **Human-Machine Interface (HMI)**

The **AI Control Unit** was further decomposed into:

```text
Sensor Fusion
      ↓
Perception
      ↓
Localization
      ↓
Prediction
      ↓
Planning
      ↓
Control
```

The architecture was modeled using SysML diagrams including:

- Requirement Diagram
- Block Definition Diagram (BDD)
- Internal Block Diagram (IBD)
- Activity Diagram
- State Machine Diagram


## 🔄 State Machine Design

The behavioral logic of the highway merge system was modeled using a state machine.

Main operational flow:

```text
Idle
  ↓
Monitoring
  ↓
Gap Evaluation
  ↓
Merge Planning
  ↓
Merge Execution
  ↓
Merge Success
```

The model also includes safety-oriented transitions for abnormal situations.

```text
Monitoring
    ↓
Emergency Braking
```

and

```text
Merge Execution
      ↓
Abort / Replan
      ↓
Merge Planning
```

This structure allows the system to continuously react to changes in the driving environment while prioritizing passenger safety and collision avoidance.


## ⏱ UPPAAL Timed Automata Modeling

The major behaviors defined in the SysML models were translated into **UPPAAL Timed Automata**.

The UPPAAL model consists of multiple templates representing individual system components:

| Template | Description |
|---|---|
| **ENV** | Driving environment and traffic conditions |
| **SEN** | Sensor and environmental data acquisition |
| **AI** | Autonomous driving decision-making |
| **BRK** | Braking and emergency braking control |
| **STR** | Steering and lane-changing control |
| **PWR** | Acceleration and propulsion control |

Interactions between components were modeled using **UPPAAL synchronization channels**.

For example:

```text
Sensor
   │
   │ collisionImminent!
   ▼
AI Controller
   │
   │ brakeCommand!
   ▼
Brake Controller
```

Clock variables, guards, invariants, and synchronization channels were used to represent real-time behavior and timing constraints.


## 🔍 Formal Verification

The system was verified using the **UPPAAL Model Checker** to evaluate properties such as:

- Deadlock freedom
- State reachability
- Safety behavior
- Timing constraints
- Successful merge completion

### Deadlock Verification

```text
A[] not deadlock
```

This property verifies that the system cannot enter a state in which all components are permanently blocked.

### Merge Reachability

```text
E<> AI.MergeSuccess
```

This property verifies that there exists an execution path in which the autonomous vehicle successfully completes the highway merge.

Verification results were analyzed to identify modeling errors and improve the interaction between system components.


## 🛠 Tech Stack

### Modeling & System Design

`SysML` `Visual Paradigm` `MBSE`

### Formal Verification

`UPPAAL` `Timed Automata` `Model Checking`

### Engineering Domain

`Cyber-Physical Systems` `Autonomous Driving` `ADAS` `Safety-Critical Systems`


## 📂 Repository Structure

```text
DCPS_group5/
│
├── Autonomous_Taxi.vpp
│   └── SysML system model
│
├── autonomous_robotaxi_uppaal.xml
│   └── UPPAAL Timed Automata model
│
├── autonomous_robotaxi_fixed.xml
│
├── autonomous_robotaxi_0525.xml
├── autonomous_robotaxi_0530.xml
├── autonomous_robotaxi_0601.xml
├── autonomous_robotaxi_0605.xml
│   └── Intermediate model versions
│
└── README.md
```


## 💡 Key Takeaways

Through this project, I gained hands-on experience in:

- Translating **system requirements into executable behavioral models**
- Designing autonomous driving systems from a **system-level perspective**
- Modeling interactions among sensing, decision-making, and vehicle control subsystems
- Applying **formal verification to safety-critical systems**
- Using UPPAAL to analyze **state reachability, deadlocks, and timing constraints**
- Identifying verification failures and refining system models accordingly
- Understanding the complete workflow from **requirements → modeling → verification**

This project strengthened my understanding of how **model-based engineering and formal verification can be applied to improve the reliability and safety of autonomous and embedded systems**.
