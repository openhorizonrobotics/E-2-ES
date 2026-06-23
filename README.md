# Embedded Systems From Source

If you've been working in robotics on the software side (writing ROS nodes, training models, planning paths) and you've wondered what's actually happening closer to the metal, this course is for you.
This is an embedded systems course built specifically for aspiring robotics engineers and mechatronics undergrads who already have a grip on basic electronics and want to go deeper into hardware. It won't hold your hand through Ohm's law. It will however, take you from microcontroller fundamentals all the way through writing device drivers, designing a PCB, and running concurrent tasks on an RTOS; all with working experiments at every step.

Everything here was built around the STM32F4 Discovery board, and experiments were run on real hardware.
Every result you see was captured on either a serial terminal or a logic analyser.
This course was developed in collaboration with Open Horizon Robotics.

---
## Course Structure

| Module | Topic                                                            |
| ------ | ---------------------------------------------------------------- |
| 1      | **Thinking Like an Embedded Engineer** (MCUs, memory, registers) |
| 2      | **Talking to Hardware** (GPIOs, registers, bitfields)            |
| 3      | **Debugging When It All Breaks**                                 |
| 4      | **Memory Matters** (RAM, Flash, stack, heap)                     |
| 5      | **Writing Your Own Drivers**                                     |
| 6      | **Project: Solve a Real Problem**                                |
| 7      | **Engineering Best Practices**                                   |
| 8      | **Intro to PCB Design**                                          |
| 9      | **Intro to Embedded OS Concepts**                                |

---
## Assets and Diagrams

All custom diagrams and screenshots are stored in the `assets/` folder and are used throughout the course with context.

- `/assets – conceptual illustrations (registers, memory maps, toolchain)`

---
## Getting Started

This is a read-first, code-later course. To follow along:

1. Clone the repo or view it on GitHub.
2. Open each module `.md` file in order.
3. Optional: Use [Obsidian](https://obsidian.md/) for a local, interactive Markdown experience.

---
## Credits

- Diagrams created using Excalidraw / draw.io / Figma.
- Reference material pulled from STMicroelectronics' official datasheets.

---
## Why This Exists

Too many embedded tutorials either:

- Skip the "why" and go straight to "copy this code"
- Assume you're already an EE grad with 10 years of experience

This course combines **clarity, practicality, and depth**, for anyone who wants to understand embedded systems from the inside out.

---
## Feedback

Got a bug, question, or insight? Open an issue or start a discussion. This course is meant to evolve with its learners.

---
