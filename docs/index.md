
### Introduction


This course is for understanding C-programming (as a systems programming language), Embedded Systems, Computer Architecture, Operating Systems, and Computer Graphics, However, the main purpose of this course is to demystifying the ESP-IDF and the ESP32 system hardware from [espressif.](https://www.espressif.com/)

#### Who is this course for?

This course is for people who have a good understanding of embedded systems programming, C and C++ programming, as well as a little bit of knowledge on Computer Graphics.


#### What is this course and why am I making it?

This course is supposed to cover everything relating to embedded systems and the ESP-IDF. So some important topics we will go over is C-programming, Operating Systems, Computer Architecture, and Computer Graphics. 

> [!question]
> Why are we covering so much C? Well since I want to write everything using the C language and since this is also a learning experience for me I want to write every lesson in C and include examples from real world projects in my lessons.

This is a course that will go through the research that I have done to make a course on embedded systems and esp32/esp-idf programming. This course will not use Adruino. 

> [!NOTE]
> *(Nothing against Adruino users hopefully this [link](https://spongebob.fandom.com/wiki/Weenie_Hut_Jr%27s) will help get you to the right place.)*

I am making this course for 2 reasons:
1. There is not a lot of good resources for esp-idf other than the official documentation.
2. This will give me motivation to do research on these topics and help me understand them as well.


#### How Can You Help

This course will of course be free :) I am trying to learn and hopefully you will learn with me. The only thing is that I ask for is engagement. Point out what I have wrong, helping me find the correct information, and give me feedback I really want to make this a helpful and reliable resource. I will allow for comment sections on my pages so that people can give feedback and corrections. When I feel comfortable with the information and completeness of this course I will create a video series that I will also make free.

#### Comments On Other Courses

The only good course I have found on esp32 and the esp-idf is [this](https://learnesp32.com/) course here. This course is great and it is a great way to get you started on embedded systems programming on the esp32 board. However, it is missing some information, espeically when it comes to rendering graphics on the [LCD displays](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/lcd/index.html). It also does not contain the optimization features that were added to [esp32-s3](https://www.espressif.com/en/products/socs/esp32-s3), which contain extra registers for specific operations. 

But again this course will also cover a lot of `C`, `C++`, `Computer Architecture`, `Operating Systems`, `Assembly Instructions`, `Embedded Systems`, and `Computer Graphics` So there will be a lot of information that here that I will cover that might have better sources. I will try to link all of my sources that I use and also identify the sources that I think are best for learning more on each topic.



#### Brief Introduction


I am a student who has a passion for the Software Engineering community and learning. I got my undergraduate in computer science from the University of Georgia, and I am currently working on my Masters at Georgia Tech. I have contributed to open source projects and have a passion for maintaining and using open source software whenever I can. I have worked with professional software for about 4 years. I am a bit of a noob when it comes to the professional enviroment but I love learning and hope that I can do and add value to the software engineering community. I also like playing league of legends, but I cant play anymore because of how addicted I get. Here are my op.ggs:

[main](https://www.op.gg/summoners/na/Abotisathot-NA1)

[testing new champs](https://www.op.gg/summoners/na/slinky%20boy-NA1)

[being a degenerate](https://www.op.gg/summoners/na/just%20freaky%20af-NA1)


#### What sets this course apart from others?

This course is a work in progress and will be kind of an open source course. It will try to go in-depth into how the esp-idf works. This course will also contain a lot of practice projects and will be focused on embedded systems programming. So all of the topics we cover like: `C`, `C++`, `Computer Architecture`, `Operating Systems`, `Assembly Instructions`,  and `Computer Graphics` will all be in the context of embedded systems. I will try to find examples in real world projects for each concept we cover that exsists within an embedded system.

For example: Lets say we are learning about buffers in C, I will provide an example of how a buffer in C is used within an embedded system.

```

    ESP_LOGI(TAG, "Initialize RGB LCD panel");
    ESP_ERROR_CHECK(esp_lcd_panel_reset(panel_handle));
    ESP_ERROR_CHECK(esp_lcd_panel_init(panel_handle));

    ESP_LOGI(TAG, "Turn on LCD backlight");
    example_bsp_set_lcd_backlight(EXAMPLE_LCD_BK_LIGHT_ON_LEVEL);

    ESP_LOGI(TAG, "Initialize LVGL library");
    lv_init();
    // create a lvgl display
    lv_display_t *display = lv_display_create(EXAMPLE_LCD_H_RES, EXAMPLE_LCD_V_RES);
    // associate the rgb panel handle to the display
    lv_display_set_user_data(display, panel_handle);
    // set color depth
    lv_display_set_color_format(display, LV_COLOR_FORMAT_RGB565);
    // create draw buffers
    void *buf1 = NULL;
    void *buf2 = NULL;
#if CONFIG_EXAMPLE_DOUBLE_FB
    ESP_LOGI(TAG, "Use frame buffers as LVGL draw buffers");
    ESP_ERROR_CHECK(esp_lcd_rgb_panel_get_frame_buffer(panel_handle, 2, &buf1, &buf2));
    // set LVGL draw buffers and direct mode
    lv_display_set_buffers(display, buf1, buf2, EXAMPLE_LCD_H_RES * EXAMPLE_LCD_V_RES * sizeof(lv_color16_t), LV_DISPLAY_RENDER_MODE_DIRECT);
```
*example from https://github.com/espressif/esp-idf/blob/master/examples/peripherals/lcd/rgb_panel/main/rgb_lcd_example_main.c*

Then I would explain the individual pieces of this code the context and how and why a buffer was used.

This course will also continually update with new technologies and I will always try and document the research that I do on these topics and how they relate to embedded systems programming.



#### What you will need for this course

Its difficult to say what you will need, because it depends on how much of this course you intend to go through. But I will list what you need in order from most important to least important


**hardware requirements:**

1. Computer running: MacOS, Windows 10 | >, Linux
2. esp32 chip
3. esp32s3 chip
4. breadboard
5. ttygo-display-t s3 or regular

Somethings you might want to make sure you are comfortable with:

1. C programming
2. Python
3. Embedded System Basics
4. Networking Basics
5. Operating System Basics
6. GPU and CPU architecture
7. Some familiarity with Assembly

WE WILL NOT USE ADRUINO.

ADRUINO HAS CLUTERRED THE WOLRD WITH ITS ADRUINONESS EVERY SEARCH FOR THESE TOPICS BRINGS UP ADRUINO STUFF



---


# What will this course cover:

## 1. The Basics

### 1.1 Computer Architecture
- ISA
- Microarchitecture
- System Design
- Assembly
- Logic Implementation
- Circuit Implementation
- Efficiency
- Processors
- Graphical Processing Units

### 1.2 C-Programming
- Basic Syntax Quick
- **Arrays**:
  - Arrays as Functions
  - Character Arrays
- **Memory**:
  - Heap vs Stack
  - Dynamic Memory Allocation
  - Everything Pointers
- **Structures**:
  - Self-Referential Structures
  - Unions
  - Bit-Fields in Structures
- File Handling
- **Advanced Memory Management and Pointers**:
  - Memory Leaks
  - Memory Management Techniques
  - Buffer Overflow
  - Security Vulnerabilities
  - Constant Pointers
  - Void Pointers
  - Function Pointer Arrays and Callbacks
- **Preprocessor Directives**:
  - Macros
  - Conditional Compilation
  - File Inclusion
  - Stringizing and Token Pasting
- **Error Handling**:
  - Error Codes
  - Assert Macros
  - Setjmp and Longjmp for Non-Local Jumps
- Multithreading and Concurrency
- Data Structures (Quick)
- OOP Concepts in C
- Procedural Programming in C
- **Networking**:
  - Sockets
  - Client-Server
  - TCP vs UDP
  - Multithreaded Network App
  - Protocols
- **Low-Level Programming**:
  - Bitwise
  - Inline Assembly
  - Memory-Mapped I/O
  - Interfacing with Hardware
  - Embedded Systems
- **C Advanced Memory for Embedded Systems**:
  - Custom Allocators
  - Memory Pools
  - Memory Alignment for SIMD and Specific Hardware
  - Memory Fragments and Defrags
  - Garbage Collection
- **C Advanced Multithreading for Embedded Systems**:
  - Lock-Free Programming
  - Thread Pools
  - Atomic Operations
  - Memory Barriers and Fences
  - Deadlock Detection and Avoidance
  - Concurrent Data Structures
- **Compilers and Linkers**:
  - Writing C Compilers and Interpreters
  - Compiler Optimization
  - Linker Scripts
  - Cross Compilation for Different Architectures
  - Code Generation and Assembly Output from C
  - IR Compiler Design
- **Embedded C**:
  - Direct Register Access
  - Writing Device Drivers
  - ISR in Embedded Systems
  - Bare Metal Programming
  - Real-Time Operating System
  - Low-Power Design and Energy-Aware Programming
- **Metaprogramming**:
  - Metaprogramming with Injection
  - Using Templates
  - Code Abstraction
- **Dynamic Libraries and Linkers**:
  - Creating and Using Shared Objects
  - Position-Independent Code
  - Inter-Process Communication
- **Advanced File System and I/O**:
  - Async I/O (AIO, epoll, kqueue)
  - Memory Mapped Files
  - High Performance I/O Techniques (DMA, Zero-Copy I/O)
- **Low-Level Debugging**:
  - Valgrind, Perf, Gprof
  - Performance Counters
  - Compiler Optimization Impact
  - Reverse Engineering of Compiled C Code
  - Stack Unwinding and Core Dump Analysis
- **Systems Programming**:
  - System Calls
  - Daemons
  - Signals and Signal Handling
  - Process Control IPC
  - Memory Protection and Virtual Memory Management
  - Writing Loadable Kernel Modules
- **Hardware-Specific**:
  - Writing Bootloaders in C
  - Firmware Development
  - AVR, ARM Cortex Microcontroller Programming
- **Optimization**:
  - Algorithmic Optimization and Profiling
  - Manual Loop Optimization
  - Cache-Friendly Code
  - SIMD
  - Processor-Specific Optimization
  - Inline Assembly

---

## 2. Embedded Systems

### 2.1 Intro
- Microcontroller vs Microprocessor
- Von Neumann Architecture
- IoT, Consumer Electronics, Automotive Devices
- Software vs Firmware

### 2.2 System Design
- Partitioning
- Environments
- Functional Prototyping and Simulations

### 2.3 Architecture
- CPU Core (RISC, CISC, ARM Cortex, etc.)
- System Buses (AMBA, AHB, APB)
- Registers, Program Counter, Stack Pointer
- Memory Maps (Code, Data, Stack, Heap)
- Memory Types (ROM, RAM, Flash, EEPROM)
- I/O Ports (GPIO, Analog vs Digital)

### 2.4 Programming Embedded Systems
- Writing Bare Metal Code (No OS)
- Writing and Debugging Firmware
- Startup Code and Initialization Sequences
- Reset and Boot Sequences
- Handling Interrupts and ISRs (Interrupt Service Routines)
- Peripheral Control Registers (Memory-Mapped I/O)

### 2.5 RTOS
- This will need its own course

### 2.6 Power Management
- Power Consumption in Embedded Systems
- Sleep Modes and Low-Power States
- Dynamic Power Scaling
- Dynamic Voltage Frequency Scaling
- Power Gating and Clock Gating
- Energy Efficient Hardware and Software

### 2.7 Interrupts and Exception Handling
- Interrupt Vector Table
- Nested Vectored Interrupt Controller
- Prioritizing Interrupts
- Software Interrupts and Traps
- Synchronous vs Asynchronous Interrupts

### 2.8 Memory Management
- Static vs Dynamic Allocation
- MPU (Memory Protection Unit)
- DMA (Direct Memory Access)
- Cache Control
- Memory Access Latency Optimization
- Non-Volatile Memory Programming

### 2.9 Peripherals and Communication Protocols
- Universal Asynchronous Receiver/Transmitter (UART)
- Serial Peripheral Interface (SPI)
- Inter-Integrated Circuit (I2C)

### 2.10 Timers

### 2.11 Bootloaders
- Understanding Bootloaders
- Customizing Bootloaders
- Booting from Flash, EEPROM, and SD Cards
- Secure Bootloaders and Cryptographic Signing
- Chain Bootloaders

---

## 3. Operating Systems

### 3.1 Processes and Threads
- Process Lifecycle
- Process Control Block
- Threads
- User-Level vs Kernel-Level Threads
- Thread Scheduling and Context Switching

### 3.2 Process Synchronization
- Race Conditions
- Critical Section Problem
- Mutexes and Semaphores
- Monitors and Condition Variables
- Deadlocks
- Inter-Process Communication

### 3.3 CPU Scheduling
- Scheduling Algorithms
- Preemptive vs Non-Preemptive Scheduling
- Multi-Level Queue Scheduling
- Multi-Processor Scheduling
- Real-Time Scheduling

### 3.4 Memory Management
- Memory Hierarchy (Registers, Cache, Main Memory, Secondary Storage)
- Paging and Segmentation
- Virtual RAM
- Page Replacement Algorithms
- Memory Allocation Techniques
- Demand Paging and Swapping

### 3.5 File Systems

### 3.6 I/O Systems
- Controllers, Ports, Buses
- Polling vs Interrupt-Driven I/O
- DMA
- I/O Scheduling
- Disk Scheduling
- RAID Levels

### 3.7 Security
- System Security
- Protection Mechanisms
- Secure Operating Systems
- Attack Vectors
- Malware and Intrusion Detection
- Secure Boot and Trusted Computing

### 3.8 Kernel Programming
- Kernel Mode vs User Mode
- System Calls
- Kernel Data Structures
- Writing Kernel-Level Modules and Drivers
- Kernel Preemption and Real-Time Kernels
- Scheduling in Kernel Space

### 3.9 Distributed Systems
- Characteristics of Distributed Systems
- Distributed File Systems
- Distributed Coordination
- Time and Clock Sync
- Distributed Process Scheduling
- CAP Theorem

---

## 4. Assembly and Basic Computer Organization

### 4.1 Assembly
- What is Assembly
- Why Use Assembly
- Machine Language vs Assembly
- Assembly Syntax
- Assembler, Linker, Loader

### 4.2 Logic Gates and Boolean Algebra
- Logic Gates (AND, OR, NOT, XOR, NAND, NOR)
- Truth Tables and Boolean Expressions
- Combinational Logic Circuits
- K-Maps
- Hardware Implementation

### 4.3 ALU (Arithmetic Logic Unit)
- Role of the ALU in the CPU
- Arithmetic Operations
- Bitwise Operations
- Signed and Unsigned Arithmetic
- Overflow and Underflow Detection in ALU
- Building an ALU with Logic Gates

### 4.4 Registers and Data Movement
- Role of Register in the CPU
- General Purpose vs Special Purpose Registers
- Register Operations
- Stack Pointer and Frame Pointer Registers
- Register Indirect Addressing
- Shift Registers and Their Use in Data Manipulation

### 4.5 Control Unit
- Role of the Control Unit in Instruction Execution
- Microprogrammed vs Hardwired Control Units
- Control Signals and Timing Diagrams
- Fetch-Decode-Execute Cycle
- Control Unit Logic Gates

### 4.6 Instruction Set Architecture
- Understanding ISA Layer
- CISC vs RISC Architecture
- Instruction Formats (OPCODE, Operands, Addressing Modes)
- Addressing Modes
- Instruction Pipelining
- Performance Implication of Different ISAs

### 4.7 x86
- x86 Registers
- x86 Instruction Set
- x86 Addressing Modes
- Stack Operations
- Floating Point Arithmetic

### 4.8 RISC
- Overview of RISC
- RISC Registers and Register Windows
- RISC Instruction Pipelining
- Load/Store Architecture
- Modern RISC Architectures (ARM, MIPS, RISC-V)

### 4.9 Assembler and Linker

### 4.10 Microprogramming

### 4.11 Floating Point Arithmetic

### 4.12 Branching and Control Flow
- Conditional and Unconditional Branching
- Loops and Jumps
- Comparing and Testing
- Call and Return
- Subroutines and Procedure Calls
- Stack Frame Management and Recursive Calls

### 4.13 Low-Level Hardware Interfacing
- Assembly with Hardware
- ISR (Interrupt Service Routine)
- Writing Device Drivers in Assembly
- Direct Memory Access (DMA)
- I/O Control

### 4.14 Advanced Control Unit Design
- Finite State Machine
- Timing and Control Clocking
- Generating Control Signals from Microinstructions
- Power Efficient Control Unit Design

### 4.15 Optimizing Assembly Code
- Loop Unrolling
- Instruction Scheduling and Reordering
- Reducing Branching Penalties
- Minimizing Memory Accesses
- SIMD

### 4.16 Emerging Architectures and Trends
- RISC-V
- Quantum Assembly
- ARM64
- VLIW
- FPGAs
- Assembly for Embedded Systems

---

## 5. Computer Graphics and Linear Algebra

### 5.1 Computer Graphics Intro
- What is Computer Graphics
- 2D vs 3D Graphics
- Graphics Libraries in C (OpenGL, Vulkan, DirectX)
- Coordinate System and Screen Space
- Pixels and Framebuffers

### 5.2 Raster Graphics
- Drawing Points and Lines (Bresenham's Line Algorithm)
- Line Clipping
- Circle and Ellipse Drawing Algorithms
- Polygon Filling Algorithms
- Antialiasing Techniques
- Bitmap Manipulation

### 5.3 3D Graphics Pipelines
- Transformations
- Homogeneous Coordinates and Perspective Division
- Viewport Transformations
- Backface Culling and Depth Buffering
- Shaders and Programmable Pipeline

### 5.4 Basic 3D Geometry
- Points, Vectors, and Normals
- Vector Operations
- Planes and Lines in 3D
- Bounding Volumes
- Ray Casting and Ray-Sphere, Ray-Plane Intersections
- Spatial Data Structures

### 5.5 Transformations
- Translation, Rotation, and Scaling
- Rotation Matrices and Quaternions
- Matrix Transformations
- Composite Transformations
- Coordinate Spaces
- Camera Models

### 5.6 Shading and Lighting
- The Phong Reflection Model
- Gouraud Shading vs Phong Shading
- Directional, Point, and Spot Lights
- Attenuation

### 5.7 Texturing

### 5.8 Graphics Optimization
- Level of Detail Techniques
- Frustum Culling and Occlusion Culling
- Optimizing the Pipeline
- Memory Management
- GPU vs CPU

### 5.9 Vectors

### 5.10 Matrices

### 5.11 Transformations

### 5.12 Functions of Several Variables

### 5.13 Gradients and Optimization

### 5.14 Multiple Integrals

### 5.15 Vector Calculus

### 5.16 Curves and Surfaces in 3D

---

## 6. The ESP-IDF

### 6.1 Introduction
- Setting Up Environment
- ESP-IDF Project Structure

### 6.2 ESP32 System Architecture
- Dual-Core Architecture
- Memory and Memory Map
- Power Management and Sleep Modes
- Clocking Systems and Clock Tree
- ROM Bootloader, Application Loading, and Execution
- App Partitioning and Bootloader Configuration

### 6.3 FreeRTOS and Multitasking
- Understanding FreeRTOS Kernel in ESP32
- Task Creation, Scheduling, and Priorities
- Synchronization (Semaphores, Queues, and Mutexes)
- Task and CPU Management:
  - Switching Between Cores
  - Memory Management
  - Performance Monitoring
- Task Notifications
- Event Groups
- Timers
- Callbacks
- High-Resolution Timers
- IPC (Inter-Process Communication)
- FreeRTOS Tickless Idle
- FreeRTOS Trace and Statistics
- Task State Monitoring
- Performance Profiling

### 6.4 GPIO and Peripherals
- Configure GPIO
- GPIO Pull-up/Pull-down Resistors
- Using GPIO Interrupts for Real-Time Events
- Using SPI Interface
- I2C Communication
- PWM and LED Control

### 6.5 ADC and DAC
- Analog to Digital Conversion (ADC)
- Digital to Analog Conversion (DAC)

### 6.6 Serial Communication
- UART
- SPI
- I2C

### 6.7 Networking with ESP32
- Wi-Fi
- TCP/IP
- UDP
- HTTP/HTTPS

### 6.8 Bluetooth

### 6.9 HTTP, HTTPS, and Web Services

### 6.10 Security and Encryption

### 6.11 File Systems
- NVS (Non-Volatile Storage)
- SPIFFS and FAT

### 6.12 OTA (Over-The-Air) Updates

### 6.13 Advanced FreeRTOS and Task Management
- Using Message Queues, Semaphores, and Event Groups
- Advanced Task Synchronization
- Memory Allocation
- Inter-Process Communication

### 6.14 Power Management

### 6.15 System Timers

### 6.16 Performance Monitoring

### 6.17 ESP-IDF Logging

### 6.18 Heap Debugging

### 6.19 Performance Optimization Techniques

### 6.20 Motor Control

### 6.21 Touch and Temperature Sensor

### 6.22 Advanced GPIO and Interrupts

---

## 7. ESP-IDF Game Development

### 7.1 Introduction

### 7.2 ESP Basic Game Loop with FreeRTOS

### 7.3 Display and Graphics Programming
- Displays
- Drawing Basic Shapes and Images
- Sprite Handling and Animation

### 7.4 User Input and Interaction
- Handling Buttons
- Touch Integration
- Input Debouncing and Response Optimization

### 7.5 Game Physics
- Collisions
- Game State Management

### 7.6 Sound Integration
- I2S for Audio Output
- Creating and Playing Sound Effects
- Controlling Volume and Audio Quality

### 7.7 Networking and Multiplayer
- Introduction to Networking in Games
- Client-Server
- Websockets

### 7.8 Graphics Optimization
- Game Loop for Real-Time Performance
- Power Resource Management

### 7.9 Game Menus

### 7.10 NVS for Saving Game States

---

## 8. ESP32-IDF Cryptocurrency

TBD






