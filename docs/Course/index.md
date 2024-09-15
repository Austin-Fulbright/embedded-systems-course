
### Introduction


This course is for understanding C-programming (as a systems programming language), Embedded Systems, Computer Architecture, Operating Systems, and Computer Graphics, However, the main purpose of this course is to demystifying the ESP-IDF and the ESP32 system hardware from [espressif.](https://www.espressif.com/)

###### Who is this course for?

This course is for people who have a good understanding of embedded systems programming, C and C++ programming, as well as a little bit of knowledge on Computer Graphics.


###### What is this course and why am I making it?

This is a course that will go through the research that I have done to make a course on embedded systems and esp32/esp-idf programming. This course will not use Adruino. 

*(Nothing against Adruino users hopefully this [link](https://spongebob.fandom.com/wiki/Weenie_Hut_Jr%27s) will help get you to the right place.)*

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


### What will this course cover:


1. The Basics
	1. Computer Architecture
		1. ISA
		2. Microachitecture
		3. System Desing
		4. Assembly
		5. logic implementation
		6. circuit implementation
		7. effeciency
		8. processors
		9. graphical processing units
	2. C-programming
		1. Basic Syntax quick
		2. Arrays
			1. arrays as functions
			2. character arrays
		3. Memory
			1. heap vs stack
			2. Dynamic memory allocation
			3. Everything pointers
		4. Structures
			1. self-referential structures
			2. Unions
			3. Bit-fields in Structures
		5. File Handling
		6. Advanced Memory Mangament and Pointers
			1. Memory Leaks
			2. Memory Mangaement Techniques
			3. Buffer Overflow
			4. Security Vulrablities
			5. Constant Pointers
			6. Void Pointers
			7. Function Pointer Arrays and Callbacks
		7. Preprocessor Directives
			1. Macros
			2. Conditional Compliation
			3. File Inclusion
			4. Stringizing and Token Pasting
		8. Error Handling
			1. Error Codes
			2. Assert Macros
			3. Setjmp and Longjmp for non-local Jumps
		9. Multithreading and Concurrency
		10. Data Structures (quick)
		11. OOP concepts in C
		12. procedural programming in C
		13. Networking
			1. sockets
			2. client-server
			3. TCP vs UDP
			4. multithreaded network app
			5. protocols
		14. Low-level programming
			1. bitwise
			2. inline Assembly
			3. memory-mapped I/O
			4. interfacing with hardware
			5. embedded systems
		15. C advanced memory for embed sys
			1. custom allocators
			2. mem pools
			3. memory allignment for SIMD and specific hardware
			4. memory frags and defrags
			5. garbage collection
		16.  C advanced multithreading for embed sys
			1. lock-free programming
			2. thread pulls
			3. atomic operations
			4. memory barriers and fences
			5. deadlock detection and avoidance
			6. concurrent data structures
		17.  Compilers and Linkers
			1. writing C compilers and interpreters
			2. Compiler optimization
			3. Linker scripts
			4. cross compilation for different architecture
			5. code generation and assembly output from c
			6. IR compiler design
		18. embedded C
			1. direct register access
			2. writing device drivers
			3. ISR in embedded systems
			4. bare metal programming
			5. real-time operating system
			6. low-power design and energy aware programming
		19. metaprogramming
			1. metaprogramming with injection
			2. using templates
			3. code abstraction
		20. dynamic libraries and linkers
			1. creating and using shared objects
			2. position independent code
			3. inter-process communication
		21. Advanced File System and I/o
			1. async i/o (AIO, epoll, kqueue)
			2. Memory Mapped Files
			3. High Preformance I/O techniques (DMA, Zero-Copy I/O)
		22. Low level debugging
			1. valgrind, perf, gprof
			2. preformance counters
			3. compiler optization impact
			4. reverse engineering of compiled C code
			5. stack unwinding and core dump analysis
		23. Systems Programming
			1. System Calls
			2. Deamons
			3. Signals and signal handling
			4. process control IPC
			5. memory protection and virtual memory managment
			6. writing loadable kernal modules
		24. Hardware-specific
			1. writing bootlaoders in C
			2. firmware development
			3. AVR, ARM Cortex microcontroller programming
		25. Optimization
			1. Algorithmic Optimization and Profiling
			2. Manual Loop Optimization
			3. Cache-Friendly code
			4. SIMD
			5. processor-specific
			6. inline assembly
	3. Embedded Systems
		1. Intro
			1. micro controller vs micro processor
			2. Von Nuemann aka Daddy
			3. IoT, Consumer electronics, Automotive devices
			4. software vs firmware
		2. system design
			1. paritioning
			2. enviroments
			3. functional prototyping and simulataitions
		3. architecture
			1. CPU Core (RISC, CISC, ARM Cortex, etc.)
			2. System Buses (AMBA, AHB, APB)
			3. Registers, Program Counter, Stack Pointer
			4. Memory Maps (Code, Data, Stack, Heap)
			5. Memory Types (ROM, RAM, Flash, EEPROM)
			6. I/O Ports (GPIO, Analog vs Digital)
		4. Programming Embedded Systems
			1. Writing Bare Metal Code (No OS)  
			2. Writing and Debugging Firmware  
			3. Startup Code and Initialization Sequences  
			4. Reset and Boot Sequences  
			5. Handling Interrupts and ISRs (Interrupt Service Routines)  
			6. Peripheral Control Registers (Memory-Mapped I/O)
		5. RTOS
			1. this will need its own course
		6. Power management
			1. power consumption in embedded systems
			2. sleep modes and low-power states
			3. dynamic power scaling
			4. dynamic voltage frequency scaling
			5. power gating and clock gating
			6. energy effecient hardware and software
		7. interrupts and exception handling
			1. interrupt vector table
			2. nested vectored interrupt controller
			3. prioritizing interrupts
			4. software interrupts and traps
			5. sync vs async
		8. Memory managment
			1. static vs dynamic allocation
			2. MPU
			3. DMA
			4. cache control
			5. Memory Access Latency Optimization
			6. non-volatile memory programming
		9. peripherals and communication protocals
			1. universail asynchronous reciever/transmitter (UART)
			2. serial peripheral interface SPI
			3. inter-integrated circuit (I2C)
		10. Timers
		11. Bootlaoders
			2. understanding bootloaders
			3. customizing bootloaders
			4. booting from flash, eeprom, and sd cards
			5. secure bootlaoders and cryptographic signing
			6. chain bootloaders
	4. Operating Systems
		1. Processes and Threads
			1. process lifecycle
			2. process control block
			3. threads
			4. user-level vs kernel level
			5. thread scheduling and context switching
		2. process synchronization
			1. race condtions
			2. critical section problem
			3. mutexes and semaphores
			4. monitors and condition variables
			5. deadlocks
			6. inter-process communication
		3. CPU scheduling
			1. scheduling algorithms
			2. preemptive vs non-preemptive scheduling
			3. multi-level queue scheduling
			4. multi-processor scheduling
			5. real-time scheduling
		4. Memory management
			1. memory heirachy (registers, cache, main memory, seconday stoage)
			2. paging and segmentation
			3. virtual ram
			4. page replacement algorithms
			5. memory allocation techniques
			6. demand page and swapping
		5. File systems
		6. I/O systems
			1. controllers, ports, busses
			2. polling vs interrupt-driven io
			3. DMA
			4. I/O scheduling
			5. disk scheduling
			6. RAID Levels
		7. Security
			1. system security
			2. protection mechnaisms
			3. secure operating systems
			4. attack vectors
			5. malware and intrustion detection
			6. secure boot and trusted computing
		8. Kernal Programming
			1. kernal mode vs user mode
			2. sys calls
			3. kernal data structures
			4. writing level modules and drivers
			5. kernel preemption and real-time kernels
			6. scheduling in kernel space
		9. distributed systems
			1. charactersics of distrubited systems
			2. distrbuted file systems
			3. disbrutied coordination
			4. time and clock sync
			5. distrbuted process scheduling
			6. CAP therom
	5. Assembly and Basic Computer Organization
		1. Assembly
			1. what is Assembly
			2. why use Assembly
			3. machine language vs assembly
			4. assembly syntax
			5. assmbler, linker, loader
		2. Logic Gates and Boolean Algrebra
			1. Logic Gates (AND, OR, NOT, XOR, NAND, NOR)
			2. Truth Tables and Boolean Expressions
			3. Combinational Logic Circuits
			4. K-maps
			5. Hardware implementation
		3. ALU (arithmetic logic unit)
			1. Role of the ALU in the CPU
			2. Arithemtic Operations
			3. Bitwise Operations
			4. signed and unsigned arithmetic
			5. overflow and undersflow detection in ALU
			6. building an ALU with logic gates
		4. Registers and Data Movement
			1. role of register in the CPU
			2. General purpose registers vs special purpose registers
			3. register operations
			4. stack pointer and frame pointer registers
			5. register indrect adressing
			6. shift registers and their use in data manipulation
		5. Control Unit
			1. role of the CU in instruction execution
			2. microprogrammed vs hardwired control units
			3. control signals and timing diagrams
			4. fetch-decode-execute Cycle
			5. control unit logic gates
		6. inscrution set arcitecture
			1. understand ISA layer
			2. CISC vs RISC architecture
			3. instruction formats (OPCODE, operands, adressing modes)
			4. adressing modes
			5. instruction pipelining
			6. preformance implication of different ISAs
		7. x86
			1. x86 registers
			2. x86 instruction set
			3. x86 addressing modes
			4. stack operations
			5. floating point arithemtic
		8. RISC
			1. overview of risc
			2. risc regisers and register windows
			3. risc instruction pipelining
			4. load/store
			5. modern risc architectures (ARM, MIPS, RISC-V)
		9. Assembler and Linker
		10. Microprogramming
		11. Floating point arithmetic
		12. Branching and Control Flow
			1. Conditional and uncoditioanl branching
			2. Loops and jumps
			3. comparing and testing
			4. call and return
			5. subroutines and procedure calls
			6. stack grame management and recursive calls
		13. low level hardware interfaceing
			1. assembly with hardware
			2. ISR
			3. writing device drivers in assembly
			4. drect memory access
			5. i/o control
		14. Advanced Control Unit Design
			1. Finite state machine
			2. timing and control clocking
			3. generating control signals from microinstructions
			4. power effeicent control unit design
		15. Optimizing Assembly Code
			1. Loop Unrolling
			2. Instruction SCheduling and Reording
			3. Reduce branching penalities
			4. Minimizing memory accesses
			5. SIMD
		16. Emerging Architectures and Trends
			1. RISC-V
			2. Quantum Assembly
			3. ARM64
			4. VLIW
			5. FPGAs
			6. Assembly for Embedded Systems
	6. Computer Graphics and Linear Algebra
		1. Computer Graphics Intro
			1. What is Computer Graphics
			2. 2d vs 3d graphics
			3. Graphics libraries in C (OpenGL, Vulkan, DirectX)
			4. coordinate system and screen space
			5. pixels and framebuffers
		2. Raster Graphics
			1. Drawing points and lines (Bresenham's line algorithm)
			2. Line clipping
			3. circile and ellipse drawing algorithms
			4. polygon filling algorithms
			5. antialising techniques
			6. bitmap manipulation
		3. 3D graphics pipelines
			1. Transformations
			2. Homogenous cordinates and perspective division
			3. viewport transformations
			4. backface culling and depth buffering
			5. shaders and programmable pipeline
		4. Basic 3D Geometry
			1. points, vectors, and normals
			2. vector operations
			3. planes and lines in 3D
			4. bounding volumes
			5. ray casing and ray-sphere, ray-plane intersections
			6. spatial data structures
		5. transformations
			1. traslation, rotation, and scaling
			2. rotation matrices and quaternions
			3. matrix transformations
			4. composite transformations
			5. coordante spaces
			6. camera models
		6. shading and lighting
			1. the phong reflection model
			2. gouraud shing vs phong shading
			3. directional, point, and spot lights
			4. attenuation
		7. textuing
		8. Graphics optimization
			1. level of detail tequiniques
			2. frustum culling occulsion culling
			3. optimize pipeline
			4. memory managment
			5. GPU vs CPU
		9. Vectors
		10. matrices
		11. transformations
		12. functions of several variables
		13. gradients and optimization
		14. multiple intergals
		15. vector calculus
		16. curves and surfaces in 3D
2. The ESP-IDF
	1. Introduction
		1. setting up enviroment
		2. ESP-IDF project structure
	2. ESP32 System Architecture
		1. Daul-core architecture
		2. Memory and Memory Map
		3. power management and sleep modes
		4. clocking systems and clock tree
		5. ROM bootloader, application loading and execution
		6. app partioning and bootloader configureation
	3. FreeRTOS and Multitasking
		1. understing FreeRTOS kernel in ESP32
		2. task creation, scheduling, and priorities
		3. synchronization (semaphores, queues, and mutexes)
		4. Task and CPU Mangement
			1. switching between cores
			2. memory management
			3. preformaing monitoring
		5. Task Notications
		6. Event Groups
		7. Timers
		8. Callbacks
		9. High-resolution Timers
		10. IPC
		11. freeRTOS tickless idl
		12. FreeRTOS trace and statiscis
		13. Task state monitoring
		14. preformanc profiling
	4. GPIO and Perhipherals
		1. Configure GPIO
		2. GPIO pull-up/pull-down resistors
		3. Using GPIO interrupts for real-time events
		4. Using SPI interface
		5. I2C communcation
		6. PWM and LED control
	5. ADC and DAC
		1. analog to digital converstion
		2. digital to analog conversion
	6. Serial COmmunication
		1. UART
		2. SPI
		3. I2C
	7. Networking with ESP32
		1. wifi
		2. TCP
		3. IP
		4. UDP
		5. HTTP
	8. Bluetooth
	9. HTTP,HTTPS, and webservices
	10. security and encryption
	11. file system
		1. nvs
		2. SPIFFS and FAT
	12. OTA updates
	13. advanced freeRTOS and Task managment
		1. using message queues, semaphores, and event groups
		2. advanced task sync
		3. memory allocation
		4. inter process comunication
	14. power management
	15. system timers
	16. preformance monitoring
	17. ESP-IDF logging
	18. Heap debugging
	19. proferomance optimization techniques
	20. Motor Control
	21. Touche and temperature secor
	22. advanced GPIO and intterupts
3. ESP-IDF Game Development
	1. Introduction
	2. ESP Basic Game Loop with FreeRTOS
	3. Display and Graphics Programming
		1. displays
		2. drawing basic shapes and images
		3. sprite handling and animation
	4. User input and interaction
		1. handling buttons
		2. touch integration
		3. input deboucing and response optimization
	5. game physics
		1. collisions
		2. game state managment
	6. sound integration
		1. I2S for audio output
		2. creaing and playing sound effects
		3. controlling volume and aduio quality
	7. networking and multiplayer
		1. introduction to networking in games
		2. client server
		3. websockets
	8. graphics optimization
		1. game loop for real time preformance
		2. power resource managment
	9. Game menus
	10. NVS for saving states
4. ESP32-IDF Cryptocurrency
	1. TBD






