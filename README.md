[Introduction_to_Computer_Organisation.docx](https://github.com/user-attachments/files/33831536/Introduction_to_Computer_Organisation.docx)
# SUMMARY: INTRODUCTION TO COMPUTER ORGANISATION AND ARCHITECTURE

### 1. Digital Computers & Radix Conversions
* **Digital Computers**: Systems that process data using variables that hold a limited number of discrete values.
* **Binary Representation**: Uses two values (`0` and `1`), called bits. This two-state system is highly reliable due to physical hardware restrictions and human logic.
* **Conversions**: 
  * **Decimal to Binary**: Solved by successive division by 2, recording remainders from Least Significant Bit (LSB) to Most Significant Bit (MSB).
  * **Binary to Decimal**: Calculated by summing the bits multiplied by their corresponding powers of 2 (base 2 positional weights).

### 2. Core Computer Definitions
* **Hardware**: The physical entity of a computer comprising electrical and electromechanical devices.
* **Software**: The programmable entity that the computer manipulates to perform data processing tasks.
* **Program**: A set of instructions given to a computer system for performing tasks.
* **Database**: The collection of data manipulated by a program.
* **System Software / OS**: An indispensable collection of programs that make effective use of the computer and bridge the gap between user needs and hardware compatibility.

### 3. Architecture, Organisation, and Design
* **Computer Architecture**: The structure and behavior of the computer as viewed by an assembly or machine language programmer (e.g., instruction formats, registers, memory access, and I/O operations).
* **Computer Organisation**: How the hardware components operate and interconnect internally to form the system during program execution.
* **Processor Organisation**: Focuses on the main internal components of a processor, how they interconnect, and how they operate.
* **Computer Design**: The hardware implementation details, specifically determining the types of hardware and their structural connectivity.

### 4. Von Neumann Architecture & Hardware Subsystems
* **Stored-Program Concept**: Instructions are encoded and stored in memory just like data, automatically fetching and decoding them to set up data paths. 
* **The Shortcoming**: At any single time, only one instruction can either be fetched or executed, creating a major performance bottleneck for modern systems.
* **Processor (CPU) Subsystems**:
  * **ALU (Arithmetic and Logic Unit)**: Manipulates data.
  * **Registers**: Small-sized, temporary data storage units.
  * **Control Unit (CU)**: Decodes instructions and generates timing/control signals to set up data paths.
* **System Interconnections**: 
  * **Main Memory (RAM)**: Usually made of dynamic RAM modules allowing the CPU to access or store binary data at random locations.
  * **Peripherals**: Input (e.g., keyboard) and output (e.g., monitor) devices.
  * **Backplane Bus**: A single communication system connecting all components using three wire types: Control wires, Address wires, and Data wires.

### 5. Performance Benchmarking
* **Execution Time Formula**: Execution Time = CPI × Clock cycle time × Number of instructions.
* **Metrics**: MIPS (Millions of Instructions Per Second) and MFLOPS (Millions of Floating-Point Operations Per Second). However, MIPS ratings are highly instruction-set dependent and vary based on the program running.
* **Synthetic Benchmarks**: Artificial programs designed to mimic real-world instruction frequencies (Arithmetic, Branch, and Memory access instructions) without computing real results. Their main limitation is that compiler writers can falsely optimize for them.
* **Standard Suites (SPEC)**: Managed by the *Standard Performance Evaluation Corporation* to offer reliable comparisons:
  * **SPEC 2000**: Evaluates client-system performance.
  * **SPEC JVM98**: Measures client-side Java Virtual Machine performance.
  * **SPEC JBB2000**: Measures server-side Java application performance.
  * **SPEC WEB2005**: Evaluates web server performance.
