# Harvard16 Microprocessor

This repository provides a structured overview, documentation, and supplemental material related to the **Harvard16 Microprocessor**, a 16-bit microprogrammed CPU developed and explored during the *Microprocessor and Microprogramming (MPMP), SoSe 2025* course at HTWK Leipzig.  
The design follows the architectural principles, instruction set concepts, and development tools introduced throughout the course and is implemented in **Logisim-Evolution**.

---

## Table of Contents

- [Overview](#overview)
- [Circuit Architecture (.circ File Structure)](#circuit-architecture-circ-file-structure)
  - [Top-Level Integration](#top-level-integration)
  - [Core Components](#core-components)
  - [External Components](#external-components)
  - [Libraries Used](#libraries-used)
- [How to Run the Project in Logisim-Evolution](#how-to-run-the-project-in-logisim-evolution)
- [Additional Notes](#additional-notes)
  - [ROM Handling](#rom-handling)
  - [Performance Considerations](#performance-considerations)
  - [Known Limitations](#known-limitations)
- [Acknowledgements](#acknowledgements)

---

## Overview

The processor represents a compact yet fully functional educational CPU. It is:

- **Microprogrammed**  
- **Turing-complete**  
- **16-bit**  
- Based on a **Harvard architecture** (separate instruction and data memories)

### Key architectural components
- 16-bit instruction format  
- **6 general-purpose registers**  
- **Stack Pointer (SP)**  
- **Program Counter (PC)**  
- A modular ALU with dedicated shift units  
- A microcode-driven Control Unit (CU)  
- Separate Program Storage ROM and Sprite ROM  
- A toolchain (WagTools) supporting assembly, testing, and documentation

The goal of the architecture is to demonstrate how a complete CPU can be constructed from fundamental digital logic while remaining accessible for laboratory work, experimentation, and educational demonstrations.

---

## Circuit Architecture (.circ File Structure)

The Logisim-Evolution project (`MpMp25.circ`) is composed of several interconnected subcircuits:

### **Top-Level Integration**
- **MAIN**  
  The central integration circuit connecting all modules, including memory components, the microcoded control path, ALU, register file, and I/O elements.

### **Core Components**
- **CU (Control Unit)**  
  A microprogrammed controller that interprets instruction fields and drives execution sequencing.

- **RF (Register File)**  
  Contains:
  - 6 general-purpose registers  
  - Stack Pointer (SP)  
  - Program Counter (PC)

- **ALU (Arithmetic Logic Unit)**  
  Supports arithmetic, logic operations, and status flag generation.

- **SHL / SHR**  
  Dedicated shift-left and shift-right units integrated into the ALU datapath.

### **External Components**
- **Program Storage ROM** – Stores machine code (`.hex` format)  
- **Sprite ROM** – Stores graphical tile and sprite data for demos (e.g., Pac-Man)  
- **Keyboard input** – Via Logisim’s virtual keyboard  
- **Clock / simulation settings** – Customizable tick frequency

### **Libraries Used**
The project depends on several built-in Logisim-Evolution libraries:
- Wiring  
- Gates  
- Plexers  
- Arithmetic  
- Memory  
- I/O  
- TTL, Base libraries  

These must remain enabled for the project to load correctly.

---

## How to Run the Project in Logisim-Evolution

Follow the instructions below to load and execute the microprocessor along with the Pac-Man demo.

1. **Install Logisim-Evolution**  
   Download from the official GitHub releases:  
   https://github.com/logisim-evolution/logisim-evolution

2. **Load the program into the Program Storage ROM**  
   - Open the `MpMp25.circ` file.  
   - Navigate to the Program Storage ROM.  
   - Right-click → **Load Image** → Select the provided `.hex` program file.

3. **Load the sprite data into the Sprite ROM**  
   - Locate the Sprite ROM.  
   - Right-click → **Load Image** → Select the sprite `.hex` file.

4. **Configure the simulation clock frequency**  
   - Go to **Simulation → Tick Frequency**  
   - Set the frequency to **2048 kHz**  
   - *(Note: On a MacBook Pro 2020 M1, effective measured tick rate ≈ 5 kHz.)*

5. **Enable continuous execution**  
   - Activate **Auto-Tick** or continuous stepping so the CPU runs instructions automatically.

6. **Enable keyboard input**  
   - Open Logisim’s **virtual keyboard**.  
   - Ensure the window is focused to allow key events.

7. **Run the Pac-Man demo**  
   - Movement: **W A S D**  
   - The demo runs natively inside Logisim using CPU-driven sprite rendering.

---

## Additional Notes

### ROM Handling
- Logisim-Evolution does **not embed** ROM contents in the `.circ` file by default.  
- The `.hex` files for program and sprites must be **reloaded** after reopening unless stored with “Include File Contents”.

### Performance Considerations
- High-frequency simulation may be limited by JVM and hardware performance.  
- Sprite rendering and CPU execution speed scale with simulation tick rate.

### Known Limitations
- Visual rendering speed varies between platforms.
- On Apple Silicon (e.g., M1 MacBook Pro), the observed practical clock frequency is around **5 kHz**

---

## Acknowledgements

This repository is based on concepts, designs, and development work originating from the  
**MPMP – Microprocessor and Microprogramming C004 (SoSe 2025)** course at **HTWK Leipzig**,  
taught by **Prof. Wagner**.

Special thanks to **all participating students**, whose collaborative effort, discussions, and tool development (particularly [**WagTools**](https://gitlab.dit.htwk-leipzig.de/mpmp-2025/microprocessor/-/tree/ludger_halpick/87440_ludger_halpick/wagtools), which made compiling the assembly code to .hex possible) enabled the creation of the microprocessor and its associated ecosystem.

