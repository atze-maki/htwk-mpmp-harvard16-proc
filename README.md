# Harvard16 Microprocessor

This repository contains documentation, notes, and supporting material related to the design of a 16-bit Harvard-architecture microprocessor as developed and explored during the MPMP course (SoSe 2025) at HTWK Leipzig.  
The processor architecture, instruction set concepts, and toolchain ideas presented here follow the principles and structures discussed during the course.

---

## Overview

The microprocessor designed in the course is a **Turing-complete**, **microprogrammed**, **16-bit Harvard-architecture CPU** implemented and simulated using **Logisim-Evolution**.  
Key architectural elements include:

- 16-bit instruction format  
- **Harvard architecture** (separate instruction and data paths)  
- **6 general-purpose registers**  
- **Stack Pointer (SP)**  
- **Program Counter (PC)**  
- A microcode-driven control unit  
- Dedicated assembler and supporting tools  

The goal of the architecture is to illustrate how a fully functional CPU can be constructed from fundamental digital logic principles while remaining compact enough for educational and experimental purposes.

---

## How to Run the Program in Logisim-Evolution

Follow the steps below to load the microprocessor project and run the Pac-Man demo inside Logisim-Evolution.

1. **Download and install Logisim-Evolution**  
   Obtain the latest release from the official repository:  
   https://github.com/logisim-evolution/logisim-evolution

2. **Load the program into the Program Storage ROM**  
   Open the CPU project in Logisim-Evolution and navigate to the instruction memory  
   (Program Storage).  
   Use the context menu → **Load Image** to load the provided `.hex` program file.

3. **Load the sprite sheet into the Sprite ROM**  
   Locate the Sprite ROM component and load the corresponding sprite `.hex` file  
   using the same **Load Image** method.

4. **Set the simulation clock frequency**  
   Go to **Simulation → Tick Frequency** and select (or manually set):  
   **2048 kHz**  
   *(On a MacBook Pro 2020 M1, the effective measured frequency is approximately 5 kHz.)*

5. **Enable continuous stepping**  
   Activate “Stepping” or “Auto-Tick” mode so the CPU executes instructions continuously.

6. **Open the integrated keyboard**  
   Click on the in-application virtual keyboard to enable input for the demo.

7. **Play the Pac-Man demo**  
   Control movement using **W A S D** keys.

Enjoy exploring the microprocessor architecture while playing Pac-Man inside Logisim-Evolution!
