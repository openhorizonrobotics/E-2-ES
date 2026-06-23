# Embedded Systems From Source

If you've been working in robotics on the software side (writing ROS nodes, training models, planning paths) and you've wondered what's actually happening closer to the metal, this course is for you.
This is an embedded systems course built specifically for aspiring robotics engineers and mechatronics undergrads who already have a grip on basic electronics and want to go deeper into hardware. It won't hold your hand through Ohm's law. It will however, take you from microcontroller fundamentals all the way through writing device drivers, designing a PCB, and running concurrent tasks on an RTOS; all with working experiments at every step.

Everything here was built around the STM32F4 Discovery board, and experiments were run on real hardware.
Every result you see was captured on either a serial terminal or a logic analyser.
This course was developed in collaboration with **Open Horizon Robotics.**

---
## Course Structure

| Module | Title                              | What It Covers                                                                     |
| ------ | ---------------------------------- | ---------------------------------------------------------------------------------- |
| 1      | Thinking Like an Embedded Engineer | MCU architecture, registers, memory maps, datasheets, the embedded toolchain       |
| 2      | Talking to Hardware                | Choosing an MCU, STM32CubeIDE, embedded workflow, SPI, I2C, ADC, PWM               |
| 3      | Debugging When It All Breaks       | Embedded debugging tools and techniques                                            |
| 4      | Memory Matters                     | RAM, Flash, stack, heap, memory architecture and failure modes                     |
| 5      | Writing Your Own Device Drivers    | Driver development from datasheets -- MPU6050, A4988, PCA9685, BME280, VL53L1      |
| 6      | Project: Solve a Real Problem      | Engineering requirements, three projects, embedded case studies                    |
| 7      | Engineering Best Practices         | MISRA, AUTOSAR, defensive programming, static analysis, code review, documentation |
| 8      | Intro to PCB Design                | KiCAD 11, schematic to layout, fabrication, assembly and bring-up                  |
| 9      | Intro to Embedded OS Concepts      | RTOS theory, FreeRTOS on STM32, tasks, mutexes, queues, semaphores                 |

---
## Read the Course

The full course is written as a GitHub Wiki. That's where all the content lives.
#  [Open the Wiki](https://github.com/openhorizonrobotics/E-2-ES/wiki)

---
## Project Files

Many of the modules include a `.zip` file containing all code and project files for that module's experiments. These are STM32CubeIDE or KiCAD projects and can be imported directly into your workspace. You'll find them in each module's directory in this repository.

---
## How This Course Was Made

Part of the writing and code in this course were produced with the assistance of **Claude**, an LLM developed by Anthropic; and **ChatGPT**, an LLM produced by OpenAI.

All written content was reviewed and edited by myself before publication. All experiment code was validated on real STM32 hardware, with results captured on a serial terminal or a logic analyser.

Many of the diagrams and figures throughout the course were designed manually in **Excalidraw**. All photographs, oscilloscope captures, and logic analyser traces were captured by hand. The Integration Board in Module 8 -- schematic, PCB layout, fabrication, assembly, and bring-up -- was designed and built from scratch.

---
## Get Involved

If this course helped you, the most valuable thing you can do is share it with someone who would benefit -- a classmate, a colleague, or anyone making the jump from robotics software into hardware.

If you find errors, have suggestions, or want to contribute, open an issue or a pull request.

If you'd like to follow what comes next, star the repository.

More about Open Horizon Robotics: https://openhorizonrobotics.com/

---