# S-400 Air Defense System Simulation (Unity)

A high-fidelity simulation of the S-400 "Triumf" air defense system in Unity.

This project implements a modular, data-driven system for radar detection, threat prioritization, and (simulated) missile engagement.

## Core Features

* **Dynamic Radar System:** A radar component scans for targets within a defined range, dynamically configured to look for specific threats.

* **Data-Driven Threat Assessment:** A threat assessment module analyzes all detected targets in real-time.

* **Weighted Scoring:** Targets are prioritized using a weighted algorithm based on:

  * Distance (closer = higher threat)

  * Speed (faster = higher threat)

  * Radar Cross-Section (RCS), defined dynamically in the Inspector.

* **Simulated Engagement:** The system logs a simulated missile launch (e.g., "40N6", "48N6DM") based on the engagement range of the highest-priority target.

## Project Overview

This system is built on two primary components that work together to create a flexible "detect and decide" loop.

A **Radar** module scans the environment for potential targets based on a list of known threat profiles. This list is provided by the "brain" of the operation, the **Threat Assessment** module.

This threat assessor continuously evaluates all detected targets, calculating a real-time "threat score" for each one based on its range, speed, and type. It then identifies the single most dangerous target and simulates an engagement order, selecting the appropriate missile type for the job. This entire process is data-driven, allowing for threat priorities to be tuned directly from the Unity Inspector without changing code.

## Future Development

This project provides the core "detect and decide" logic. The next steps, based on the original design document, are:

* **Missile Launchers:** Create launcher prefabs that receive engagement orders from the `ThreatAssessmentSystem`.

* **Homing Missiles:** Develop missile prefabs with `Rigidbody` and a PID-based guidance script (`HomingMissile.cs`) to seek and destroy their assigned targets.

* **Object Pooling:** Implement a pooling system for missiles to improve performance.

* **Electronic Warfare (EW):** Simulate jammers that can increase the `detectionThreshold` of the radar.

* **C&C Interface:** Build a UI to visualize the radar picture and engagement status.
