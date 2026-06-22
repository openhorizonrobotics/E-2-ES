In June 2025, this course started with a question that sounds almost too simple to take seriously: what actually happens when a microcontroller runs your code? After a year, the course is now complete, and ready for your perusal.  

- **Module 1** answered that question from first principles with block diagrams, memory maps, register definitions, and careful datasheet reading. 
- **Module 2** put that knowledge to work -- choosing a real MCU family, setting up a real toolchain, and talking to real peripherals over SPI, I2C, ADC, and PWM.
- **Module 3** was about what happens when things go wrong, which in embedded systems is often and unpredictably. Debugging is a skill that textbooks tend to undervalue.
- **Module 4** went deeper into the memory architecture that underlies everything -- stack, heap, flash, RAM -- and the failure modes that emerge when you don't understand where your data actually lives.
- **Module 5** is where the course asked something harder: given a datasheet and a blank .c file, can you make a completely unfamiliar device work? You read the documentation, understood the register maps, wrote the drivers, and ran the experiments.
- **Module 6** stepped back from the hardware and asked engineering questions rather than a programming ones: what problem are we actually solving, and have we thought rigorously enough about the requirements before writing a single line of code? The three projects and case studies in that module were about developing the judgement to ask the right questions before committing to an implementation.
- **Module 7** was perhaps the most unusual module in the course -- a look at how professional production code in robotics and automotive contexts differs from the kind of code most engineers write when they're learning. MISRA, AUTOSAR, the C++ abstract machine, defensive programming, static analysis, documentation, code review. 
- **Module 8** took everything off the screen and onto a PCB. The Integration Board -- designed in KiCAD, fabricated at Lion Circuits, and assembled by hand on a workbench -- is the most concrete artifact this course produced. It's not perfect, but the issues with it are documented in the text. Real engineering projects have both of those things. Pretending otherwise would have been a disservice.
- **Module 9** used that board to demonstrate what an RTOS actually is and why it exists -- as a working system with five concurrent tasks, shared bus arbitration, inter-task data pipelines, and semaphore-based coordination running on the same STM32F407 that has been at the centre of the course since Module 2.

This arc -- from register maps to RTOS, from a blinking LED to a fabricated PCB -- is what this course set out to cover. 
**It doesn't cover everything.** Signal integrity, power electronics, advanced motor control, communication stacks, safety certification -- these are real topics that a working embedded or robotics engineer will eventually need. But this course was never trying to be everything. It was trying to give you enough of a foundation to teach yourself the rest, and enough hands-on experience to trust that foundation when you lean on it.

All of the content, code, schematics, and project files are available on GitHub. Everything is open and free to use.

If this course helped you, the best thing you can do is share it with someone it might help next.

---