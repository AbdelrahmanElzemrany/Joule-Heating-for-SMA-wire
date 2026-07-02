[Click here and press view raw to download and view the simulation video explaining the standalone process.](StandaloneJouleHeatingExplaination.mp4)

[Click here and press view raw to download and view the integrated control loop video.](TheFeedForwardControllerWithJouleheating.mp4)

# Joule-Heating-for-SMA-wire

An end-to-end electro-thermal modeling framework and feedforward control architecture to validate Joule heating dynamics in standalone and integrated Shape Memory Alloy (SMA) bending actuators. Built using Simulink, Simscape Multibody, and MATLAB.

This repository focuses explicitly on validating the thermodynamic subsystem and evaluating its integration with a feedforward control system utilizing lookup tables extracted via First-Order Reversal Curves (FORC). 

## 🚀 Pipeline & File Architecture

The repository is structured sequentially to take a robot from raw thermodynamic equations to a verified controller tracking trajectories:

### 1. Kinematic & Symbolic Modeling
* **`Joule heating for SMA wire.pdf`**: Establishes the governing electro-thermal differential equations, incorporating sensible heat storage, Joule heating inputs, and passive environmental convective dissipation.
* **`sma_pure_1d_switching.mat`**: MATLAB workspace data file containing the numerical datasets and lookup matrices extracted via First-Order Reversal Curves (FORC) to drive the feedforward control loops.

### 2. Trajectory Generation & Data Extraction
* **`StandAloneJouleHeatingSystem.slx`**: Isolated Simulink plant model used to verify baseline transient thermal responses. Implements a closed-loop PID controller regulating a 12V/6V PWM duty cycle against convective heat losses.

### 3. Dynamics & Identification
* **`FeedForwardControllerAndTheJouleHeatingSystem.slx`**: The fully integrated multi-physics system. Incorporates metallurgical latent heat of transformation enthalpy into the plant dynamics to model material buffering. Features a feedforward mapping loop that queries the FORC data arrays to convert curvature targets into explicit temperature targets, completely eliminating feedback loop phase confusion.
