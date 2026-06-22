# PID-101

A hands-on series of Python simulations + explanations to understand PID (Proportional-Integral-Derivative) control. Ideal for engineering students, hobbyists, or anyone curious about control systems.

---

##  Table of Contents

1. [About](#about)  
2. [What You’ll Learn](#what-youll-learn)  
3. [How to Use This Repo](#how-to-use-this-repo)  
4. [Experiments / Simulations](#experiments--simulations)  
5. [Play & Extend](#play--extend)  
6. [Prerequisites](#prerequisites)  
7. [Getting Started](#getting-started)  
8. [Contributing](#contributing)  
9. [License & Contact](#license--contact)

---

## About

This module is a learning resource with code + commentary to help you understand PID control in various systems. Each simulation builds in complexity:

- Translating PID from theory → code  
- Simulating response, observing error, overshoot, steady-state behaviour  
- Comparing open vs closed loop systems  
- Moving from first-order systems to second-order, thermal, mechanical, etc.


---

## What You’ll Learn

- How each term of PID (P, I, D) influences system behaviour.  
- Real effects like overshoot, settling time, oscillation, steady-state error  
- Differences between open-loop vs closed-loop feedback control  
- Modeling of first-order and second-order dynamics  
- How to tune PID gains in simulation to see what works (and what doesn’t)

---

## How to Use This Repo

1. Pick an experiment file.  
2. Read the explanation (markdown) to understand the system model.  
3. Run the Python script to see the simulation.  
4. Change PID gains / system parameters. Observe how the response changes (plot, print, etc.). 
5. (Optional) Modify the system model or combine features from different examples.

---

## Experiments / Simulations

| Experiment                      | Description                                                     |
| ------------------------------- | --------------------------------------------------------------- |
| **1. First-Order DC Motor**     | Simple model; see how P, I, D affect step response.             |
| **2. Thermal Systems**          | Heating/cooling dynamics; environmental losses; time constants. |
| **3. Open-Loop vs Closed-Loop** | Why feedback matters; compare both.                             |
| **4. Spring-Mass-Damper**       | Second-order dynamics; oscillations and damping.                |

---

## Prerequisites

- Python 3.x  
- Libraries: `numpy`, `matplotlib` (or equivalent)  
- Basic knowledge: differential equations, basic control theory

---

## Getting Started

```
bash
git clone https://github.com/mukul160/PID-.git
cd PID-
cd Experiments/1_first_order_dc_motor
python simulation.py
``````


---
