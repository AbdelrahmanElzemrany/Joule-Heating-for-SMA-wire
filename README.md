[Click here and press view raw to download and view the simulation video explaining the standalone process.](StandaloneJouleHeatingExplaination.mp4)

[Click here and press view raw to download and view the integrated control loop video.](TheFeedForwardControllerWithJouleheating.mp4)

# Joule-Heating-for-SMA-wire

An end-to-end electro-thermal modeling framework and feedforward control architecture to validate Joule heating dynamics in standalone and integrated Shape Memory Alloy (SMA) bending actuators. Built using Simulink, Simscape Multibody, and MATLAB.

This repository focuses explicitly on validating the thermodynamic subsystem and evaluating its integration with a feedforward control system utilizing lookup tables extracted via First-Order Reversal Curves (FORC). 
## 📝 Project Overview

While idealized models treat temperature as a direct input signal, real-world Shape Memory Alloy (SMA) actuators must be driven via electrical current (Joule heating). This introduces complex **electro-thermal dynamics** and severe physical lag caused by hardware voltage limits, convective environmental cooling rates, and structural latent heat of transformation. During phase transitions, the material absorbs or releases latent heat, acting as a thermal buffer that severely distorts standard linear temperature control and worsens tracking errors.

This project bridges the gap between material theory and hardware reality by developing an end-to-end **electro-thermal modeling and feedforward control framework**. The system models the complete energy balance—balancing electrical power inputs ($I^2R$) against transient sensible heat storage, latent heat enthalpy blocks, and ambient convective dissipation. By integrating this high-fidelity plant model with a path-dependent feedforward controller driven by pre-extracted First-Order Reversal Curve (FORC) lookup arrays, the architecture maps curvature targets into explicit current/voltage commands. This completely eliminates feedback phase confusion and mitigates the destructive lag of physical thermal buffering.

<img width="1160" height="716" alt="Standalone" src="https://github.com/user-attachments/assets/2f0fc0fb-2d97-478a-bfd4-cf67dc26fd26" />
Figure 1 A standalone Joule heating system as seperated system before the intgeration with the FORC extraced look up tables controller 


<img width="1000" height="650" alt="GovereningEquations" src="https://github.com/user-attachments/assets/19ed0761-81bd-4f45-9ed4-4920bfbb1093" />
Figure 2 The governing equations of the electro-thermal system


<img width="1917" height="926" alt="StandAloneJouleHeatingResponse" src="https://github.com/user-attachments/assets/78e48add-3863-4fc5-b1c8-328384d5fb1a" />
Figure 3 The behavior analysis of the standalone Joule heating system

<img width="1745" height="597" alt="image" src="https://github.com/user-attachments/assets/94111f12-9cfc-44a4-b92a-cf780afbab5e" />
Figure 4 FeedForward Configuration with thr integeration of the joule heating system


<img width="1885" height="890" alt="FeedRes" src="https://github.com/user-attachments/assets/e49a5930-0c3a-4246-8efe-1365afeec24d" />
Figure 5 The behavior analysis of the system





## 🚀 Pipeline & File Architecture

The repository is structured sequentially to take a robot from raw thermodynamic equations to a verified controller tracking trajectories:

### 1. Kinematic & Symbolic Modeling
* **`Joule heating for SMA wire.pdf`**: Establishes the governing electro-thermal differential equations, incorporating sensible heat storage, Joule heating inputs, and passive environmental convective dissipation.
* **`sma_pure_1d_switching.mat`**: MATLAB workspace data file containing the numerical datasets and lookup matrices extracted via First-Order Reversal Curves (FORC) to drive the feedforward control loops.

### 2. Trajectory Generation & Data Extraction
* **`StandAloneJouleHeatingSystem.slx`**: Isolated Simulink plant model used to verify baseline transient thermal responses. Implements a closed-loop PID controller regulating a 12V/6V PWM duty cycle against convective heat losses.

### 3. Dynamics & Identification
* **`FeedForwardControllerAndTheJouleHeatingSystem.slx`**: The fully integrated multi-physics system. Incorporates metallurgical latent heat of transformation enthalpy into the plant dynamics to model material buffering. Features a feedforward mapping loop that queries the FORC data arrays to convert curvature targets into explicit temperature targets, completely eliminating feedback loop phase confusion.
