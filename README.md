# Embedded Systems from Source

Welcome to **Embedded Systems from Source** — a hands-on, diagram-rich, and concept-first guide to mastering embedded systems through real-world thinking and bare-metal coding.

Whether you're a student, an engineer returning to the basics, or a robotics enthusiast tired of YouTube rabbit holes — this course is for you.

---
## What You'll Learn

- How microcontrollers actually work — not just how to use libraries
- Pointers, memory maps, and register-level control
- GPIO, timers, interrupts, and serial protocols (USART, I2C, SPI)
- The startup sequence and what happens before `main()`
- How to debug embedded systems like an engineer, not a guesser
- Toolchain pipeline: from code to binary to flash
- How to read a datasheet without your eyes glazing over
- (And eventually) how to write your own drivers

> All content is structured in **progressive modules** with annotated code examples and original diagrams.

**Click here to jump to your desired module in the Repository!**
<li><a href="Module_1/Learning%20Outcomes.md">Module 1: Thinking Like an Embedded Engineer</a></li>
<li><a href="Module_2/Learning%20Outcomes.md">Module 2: Talking to Hardware</a></li>


**OR**

Read the content in the [wiki](https://github.com/openhorizonrobotics/E-2-ES/wiki/02.-Module1_WhatIsBareMetalProgramming)!

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

> Bonus: Code samples are provided in `/Module_1/CodeExamples` and written for the STM32F103 (Blue Pill), and the STM32F407 Discovery Board.

---
## Credits

- Diagrams created using Excalidraw / draw.io / Figma.
- Reference material pulled from STMicroelectronics' official datasheets.

---
## Why This Exists

Too many embedded tutorials either:

- Skip the "why" and go straight to "copy this code"
- Assume you're already an EE grad with 10 years of experience

This course bridges the gap — combining **clarity, practicality, and depth** — for anyone who wants to understand embedded systems from the inside out.

---
## Feedback

Got a bug, question, or insight? Open an issue or start a discussion — this course is meant to evolve with its learners.

---