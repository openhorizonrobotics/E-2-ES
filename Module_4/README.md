From this module, you'll learn:

### Chapter 1: Memory Architecture and Layout -- What Memory Exists and Why

- Establish the physical and architectural reality of microcontroller memory.
- Cover regions like Flash, SRAM, System and Peripheral Memory
- Explain the difference between instruction and data memory.
- Why Memory Speeds Differ
- Stack, Heap, Global/Static Variables, How the Linker Script Defines thier Placement
- Why Stack and Heap Collisions are Catastrophic
- Clarify Common Misconceptions

### Chapter 2: Memory at Runtime -- How Memory Is Used While the System Runs

- Explain stack growth, function calls, interrupts, context switching, and how local variables, return addresses, and saved registers consume stack space.
- Heap allocation, fragmentation, and why `malloc` is often avoided or tightly controlled in embedded systems.
- Introduce DMA, cache (if applicable), and how peripherals access memory independently of the CPU.
- Discuss concurrency hazards: Shared buffers, volatile qualifiers, alignment, and memory consistency.
- Explain runtime consequences: How seemingly small design decisions lead to stack overflows, data corruption, or timing issues.

### Chapter 3: Memory Failures and Debugging -- How Memory Breaks and How to Diagnose It

- Discuss common memory-related faults such as stack overflow, heap exhaustion, buffer overruns, use-after-free, and invalid pointer access.
- Tie these directly to real MCU behavior: HardFaults, BusFaults, silent corruption, or watchdog resets.
- Explain how to debug these issues using map files, linker symbols, register inspection, fault status registers, watchpoints, and stack frame analysis.
- Strategies for memory catastrophe prevention, such as stack sizing, guard patterns, static analysis, and disciplined allocation policies.