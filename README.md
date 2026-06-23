# Embedded Systems From Source

<p align="center">
<img height="150" alt="image" src="https://github.com/user-attachments/assets/0fea4c0a-3b52-4a89-a596-89d595b98dbe" />
<img height="150" alt="image" src="https://github.com/user-attachments/assets/9c009e89-57f6-4a77-bb4b-9e8a5fd2f33a" />
<img height="150" alt="image" src="https://github.com/user-attachments/assets/819b4400-81a5-4c02-9f33-e9e74eadb87b" />
<img height="180" alt="image" src="https://github.com/user-attachments/assets/7829ec49-e25c-454f-9f81-f1ecf9e696e9" />
<img height="180" alt="image" src="https://github.com/user-attachments/assets/ca55c03d-e2a0-4379-825e-1f27169991d9" />
<img height="180" alt="image" src="https://github.com/user-attachments/assets/8b10cd63-6c59-4391-9c37-2e1f4d7e416b" />
</p>
If you've been working in robotics on the software side (writing ROS nodes, training models, planning paths) and you've wondered what's actually happening closer to the metal, this course is for you.<br>
This is an embedded systems course built specifically for aspiring robotics engineers and mechatronics undergrads who already have a grip on basic electronics and want to go deeper into hardware.<br>
It won't hold your hand through Ohm's law. It will however, take you from microcontroller fundamentals all the way through writing device drivers, designing a PCB, and running concurrent tasks on an RTOS; all with working experiments at every step.<br><br/>
The images here are a glimpse of what you can expect:
<br><br/>
<p align="center">
<img height="160" alt="image" src="https://github.com/user-attachments/assets/2e68ddf3-8c4e-44d8-85e2-e4a0fb0f3a03" />
<img height="160" alt="image" src="https://github.com/user-attachments/assets/36d1362b-3d3f-4eb4-b0ed-57f73cb0c5de" />
<img height="200" alt="image" src="https://github.com/user-attachments/assets/a0132d9d-8648-4ca8-8964-0eeba6831631" />
<img height="200" alt="image" src="https://github.com/user-attachments/assets/2293b908-802c-4ec2-a5bc-844761a838a1" />
</p>
Everything here was built around the STM32F4 Discovery board, and experiments were run on real hardware.
Every result you see was captured on either a serial terminal or a logic analyser.
This course was developed in collaboration with Open Horizon Robotics.
<br><br/>
<p align="center">
<img height="210" alt="image" src="https://github.com/user-attachments/assets/8343a280-5d73-495e-be41-afa75355c688" />
<img height="210" alt="image" src="https://github.com/user-attachments/assets/c0054387-9e3e-429a-a06d-83c8fd58bb34" />
<img height="210" alt="image" src="https://github.com/user-attachments/assets/356e0343-721a-4013-a29f-e23d195c54c2" />
<img height="210" alt="image" src="https://github.com/user-attachments/assets/25a3693e-6fde-4e0c-93b7-65799b735f78" />
<img height="250" alt="image" src="https://github.com/user-attachments/assets/7d1bdfdc-98b8-4db1-a48a-21d7f0021ce4" />
<img height="250" alt="image" src="https://github.com/openhorizonrobotics/E-2-ES/raw/main/Module_9/Assets_9/15.gif" />
</p>

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

<h3 align="center">
  <a href="https://github.com/openhorizonrobotics/E-2-ES/wiki">CLICK HERE FOR THE ESS WIKI</a>
</h3>
<br><br/>

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
