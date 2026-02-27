# Pressure Modeling and Control

## Introduction

This project implements a complete pressure control system using PID and cascade control strategies. The system identifies the transfer function of a physical pressure control platform through experimental testing, designs appropriate controllers, and validates performance both in simulation (MATLAB/Simulink) and on real hardware.

## Transfer function identification from step response experiments

To ensure measurement reliability, three identical experimental runs were performed with the same command value of 150. Each measurement was filtered using a low-pass filter to remove noise and measurement artifacts. The three filtered signals were then averaged to produce a single representative response curve. This averaged signal exhibited smooth dynamics without significant fluctuations, making it suitable for transfer function identification. From this final averaged curve, the physical model parameters were extracted, including the steady-state gain, time constant, and system dynamics, which were used to derive the transfer function Hp of the pressure control process.

<p align="center">
  <img src="graphics/Intitial_responses.png" width="45%" />
  <img src="graphics/avarage_response.png" width="45%" />
</p>

The pressure control platform was tested using step commands to characterize system behavior. Three experimental runs were conducted with a reference value of 150 to ensure accurate parameter estimation. However, the system consistently reached a steady-state value of 142, revealing an inherent steady-state error of 8 units. This discrepancy between the commanded value (150) and the achieved output (142) indicated the need for a controller capable of eliminating steady-state error, which motivated the selection of a PID controller with unity gain (Kp = 1) to achieve zero steady-state error in the final implementation.

From the averaged response, the transfer function parameters were calculated:

$$K = \frac{y_{st}}{u} = 0.95$$

$$T = \frac{t_t}{3.9} = 1.8$$

where $y_{st}$ is the steady-state output change, $u$ is the input step change, and $t_t$ is the transient time.

<p align="center">
  <img src="graphics/transfer_function.png" width="60%" />
</p>

The identified transfer function response matches the averaged experimental data, confirming successful model identification of the physical installation.
