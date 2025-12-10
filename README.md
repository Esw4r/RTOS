# Implementation of RTOS for Smart Home Control

## Repository Structure

    / (root)
    ├── Core/                               # Main application code, ADC, tasks, sensor handling
    ├── Drivers/                            # HAL drivers, board-specific code
    ├── Middlewares/Third_Party/FreeRTOS/Source/   # RTOS kernel sources
    ├── .project, .cproject, .mxproject     # STM32CubeIDE project files
    ├── STM32F401CCU6_FLASH.ld              # Linker script / memory layout
    └── README.md                           # (this file)

## How to Build & Flash

1. **Clone the repository**
    ```bash
    git clone https://github.com/Esw4r/RTOS.git
    cd RTOS
    ```
2. **Open the project** in STM32CubeIDE  
   (or import as an existing workspace project — `.project`, `.cproject`, and `.mxproject` are included)
3. **Configure hardware **
   - The Configuration for the current setup is given below
5. **Build the project**  
   Compile and link using STM32CubeIDE's build option
6. **Flash to the MCU**  
   Use **ST-LINK** or the IDE's built-in debugger/flashing tools
7. **Run**
      
## What is RTOS?
RTOS stands for Real-Time Operating System — basically, it’s an operating system with a strict sense of timing.
Unlike General Purpose which addresses a certain task only when its possibly can, RTOS will get to the task right on the scheduled time. Thats why its called "Real" Time OS.

#### Multitasking in RTOS
As our STM32F401CCU6 has only one hardware thread, Multi-threading is impossible here. The CPU runs one task at a time, but the RTOS switches between tasks so quickly it feels like they run in parallel.
- Each task gets CPU time according to its priority and scheduling policy.
- The RTOS uses a scheduler and context switching to make this happen.

---
### 3 Default Primary Tasks Assigned:
- Default Task
- Task2
- Task3
  
 **Default Task** - Indicated the working of the RTOS by setting the PB7 Led to ON
 
 __Task 2__ - LDR with Led 
 
 **Task 3** - LM35 (Temperature Sensor) with USART2

---
## Default Setup

#### Hardware Components Used
- STM32F401CCU6
- LM35 - Temperature Sensor
- GL5528 - LDR
- USART2
- 2x LED
- Resistor (For stable LDR data reading)

#### Pin Configurations - STM32F402CCU6

PA0 -> LM35(Temp Sensor) - ADC1IN0
PA1 -> GL5528 (LDR) - ADC1IN1
PA2 -> USART2 RX
PA3 -> USART2 TX
PB6 -> LED (startup)
PB7 -> LED (config with LDR)

---
