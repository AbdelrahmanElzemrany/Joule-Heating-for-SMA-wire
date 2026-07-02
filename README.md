[Click here and press view raw to download and view the simulation video explaining the standalone process.](StandaloneJouleHeatingExplanation.mp4)
[Click here and press view raw to download and view the integrated control loop video.](TheFeedForwardControllerWithJouleheating.mp4)

# Joule-Heating-for-SMA-wire

An end-to-end electro-thermal modeling framework and feedforward control architecture to validate Joule heating dynamics in standalone and integrated Shape Memory Alloy (SMA) bending actuators. Built using Simulink, Simscape Multibody, and MATLAB.

## 🚀 Pipeline & File Architecture

The repository is structured sequentially to take a robot from raw thermodynamic equations to a verified controller tracking trajectories:

### 1. Kinematic & Symbolic Modeling
* **`Joule heating for SMA wire.pdf`**: Establishes the governing electro-thermal differential equations, incorporating sensible heat storage, Joule heating inputs, and passive environmental convective dissipation.

### 2. Trajectory Generation & Data Extraction
* **`jouleheating.slx`**: Isolated Simulink plant model used to verify baseline transient thermal responses. Implements a closed-loop PID controller regulating a 12V/6V PWM duty cycle against convective heat losses.

### 3. Dynamics & Identification
* **`FinalShapewithjouleheating.slx`**: The fully integrated multi-physics system. Incorporates metallurgical latent heat of transformation enthalpy into the plant dynamics to model material buffering. Features a feedforward lookup table that translates reference curvature trajectories into explicit temperature targets to eliminate feedback loop phase confusion.
