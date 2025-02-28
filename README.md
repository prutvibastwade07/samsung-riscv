# samsung-riscv
RISC-V Talent Development Program, powered by Samsung Semiconductor India Research (SSIR) along with VLSI System Design (VSD)
# samsung-riscv
The program is based on the RISC-V architecture and uses open-source tools for VLSI chip design and RISC-V.

## Basic Details

Name: Pruthvi Chidanand Bastwade

College: Vidyavardhaka College of Engineering

Email ID: pruthvicb7@gmail.com

GitHub Profile: [prutvibastwade07](https://github.com/prutvibastwade07)

## Task 1: Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler

## C and RISC-V Based Labs

This repository demonstrates the processes involved in compiling C programs and generating assembly code using both a standard GCC compiler and a RISC-V GCC compiler. It includes comprehensive steps and explanations to guide users through each stage of the compilation and debugging workflow.

## C Language-Based Lab

### Steps to Compile a .c File on Your Machine:

1. Open the bash terminal and navigate to the directory where you want to create your file.
2. Use the following command to create and edit a new .c file:
   sh
   gedit sum_1ton.c
![sum1ton_code_snippet](https://github.com/user-attachments/assets/94e9fe3c-9fae-44db-bd99-7d4ecbdc5ee6)
)
### Steps to Compile a .c File :
 sh
 gcc sum_1ton.c
 ./a.out

### Compilation and execution complete.

![sum1ton_output](https://github.com/user-attachments/assets/25d12a47-081d-42f0-960d-afa3895b13c5)
)


## RISC-V Based Lab

### Steps to Compile Using RISC-V GCC Compiler:
1. Ensure the RISC-V GCC compiler is installed and accessible on your system.
2. Verify the .c file contents using the cat command:
sh
cat sum_1ton.c

![cat_sum1ton](https://github.com/user-attachments/assets/b31f0725-370d-48e9-875c-061d3c58444a)
)

4. Compile the C program for RISC-V architecture using:
 sh
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum_1ton.o sum_1ton.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

![O1 and Ofast](https://github.com/user-attachments/assets/e716cc22-f186-4c72-b6ef-8bd8f8214645)
)


5. Disassemble the object file to view its assembly code using:
 sh
riscv64-unknown-elf-objdump -d sum_1ton.o
```
6. Use /main in the terminal to locate the main function in the assembly output.
![assembly_code_snippet](https://github.com/user-attachments/assets/98ebc243-65f5-441a-8e8e-dc1353a18050)

### Explanation of Commands and Options: 
1. -mabi=lp64: Specifies the Application Binary Interface (ABI) for 64-bit integers, pointers, and long data types, suitable for 64-bit RISC-V architecture.

2. -march=rv64i: Indicates the 64-bit RISC-V base integer instruction set architecture.

3. -O1: Enables basic optimization for better performance without significantly increasing compilation time.
  
4. -Ofast: Focuses on maximizing performance by enabling aggressive optimizations, potentially at the cost of standard compliance.

5. riscv64-unknown-elf-objdump: A tool for disassembling RISC-V binaries to examine the code structure and debug it effectively.


## Task 2: Task is to refer to review the provided spike simulation and observing performance under the -Ofast and O1 compiler optimization flagzs
# RISC-V Instruction Types for the Given Code
<details>
<summary><b>Task 2:</b>Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler simulator</summary>
<br>
	
**Debugging with SPIKE: Comparing -O1 and -Ofast Optimizations**

**-O1:** A moderate optimization for balanced performance.

**-Ofast:** A high-speed optimization that prioritizes performance over strict standards

**add.c File**
![sum code](https://github.com/user-attachments/assets/8989da87-e34d-4330-af71-683b478b9642)

Commands:

riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum.o sum.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum.o sum.c

![Debugging O1](https://github.com/user-attachments/assets/905f4204-0931-4323-8e43-253e8a263ad1)

![Debugging Ofast](https://github.com/user-attachments/assets/94d7b72b-af71-44a5-be81-52251a9d8e75)


**Running on SPIKE**

Commands:

spike pk sum.o

To open Interactive Debugging

spike -d pk sum.o

Objdump:

riscv64-unknown-elf-objdump -d sum.o
riscv64-unknown-elf-objdump -d sum.o | less
```
![Objdump -O1](https://github.com/user-attachments/assets/057054e4-16f8-42b0-a7cb-d51486dfa856)

![Objdump -Ofast](https://github.com/user-attachments/assets/b7874894-8ed7-42a7-907d-deee09188ec4)

</details>
</details>
<details>
   
## Task 3: Task is to refer to review the RISC-5 software documentation to undersytand the R,I,S,B,J,U instruction types.
# RISC-V Instruction Types for the Given Code

## *Instruction Types*

### 1. *R-Type (Register-Register Instructions)*
   - Typically involves arithmetic and logical operations between registers.
   - No such instruction appears directly in the given code at the C level, but operations like comparisons (e.g., num <= 0.0) may involve R-type instructions at the assembly level.

### 2. *I-Type (Immediate Instructions)*
   - Used for instructions with immediate values or memory addressing.
   - Example in the code: scanf("%lf", &num);
     - This would translate to an I-type instruction to load the address of num or handle immediate values.

### 3. *S-Type (Store Instructions)*
   - Used for storing data from a register to memory.
   - Example: Assigning the value entered by the user into the variable num involves S-type instructions.

### 4. *B-Type (Branch Instructions)*
   - Used for conditional branching.
   - Examples:
     - if (num <= 0.0)
     - if (num == 0.0)
     - These conditions are compiled into B-type instructions such as BEQ (branch if equal), BLT (branch if less than), or BGE (branch if greater or equal).

### 5. *J-Type (Jump Instructions)*
   - Used for unconditional jumps.
   - Example: The else block in the code could lead to a jump instruction to skip over the if block or jump to the end of the program.

### 6. *U-Type (Upper Immediate Instructions)*
   - Used for loading upper bits of immediate values.
   - While not directly visible in the C code, U-type instructions like LUI (load upper immediate) might be used during address calculations or handling larger constants.

### 7. *UJ-Type (Unconditional Jump and Link Instructions)*
   - Similar to J-type but used for function calls.
   - Example: The main() function or calls to printf and scanf might involve UJ-type instructions like JAL (jump and link).

---
This classification provides a detailed mapping of the instruction types based on the given C code.

Task 4: Functional Simulation of RISC-V Core

RV32I Pipelined Processor Implementation

Overview

This Verilog module, iiitb_rv32i, implements a simplified pipelined processor based on the RV32I instruction set architecture (ISA). The design consists of five pipeline stages: Instruction Fetch (IF), Instruction Decode (ID), Execution (EX), Memory (MEM), and Write Back (WB). The processor supports arithmetic, logical, memory, and branch instructions.

Module Description

Inputs:

clk: Clock signal

RN: Reset signal

Outputs:

NPC: Next Program Counter value

WB_OUT: Write Back output

Registers & Memories:

REG: Register file (32 registers, 32-bit each)

MEM: Instruction memory (32 locations, 32-bit each)

DM: Data memory (32 locations, 32-bit each)

Pipeline Stages

Instruction Fetch (IF):

Fetches the instruction from memory based on NPC.

Updates NPC for the next cycle.

Instruction Decode (ID):

Decodes the fetched instruction.

Reads values from the register file.

Computes immediate values if needed.

Execution (EX):

Performs ALU operations for arithmetic and logical instructions.

Computes memory addresses for load/store instructions.

Evaluates branch conditions.

Memory Access (MEM):

Reads from or writes to data memory for load/store instructions.

Passes ALU results to the next stage.

Write Back (WB):

Writes results back to the register file.

Updates the output WB_OUT.

Supported Instructions

Arithmetic & Logical (Register & Immediate): ADD, SUB, AND, OR, XOR, SLT, ADDI, SUBI, ANDI, ORI, XORI

Memory Access: LW (Load Word), SW (Store Word)

Branching: BEQ (Branch if Equal), BNE (Branch if Not Equal)

Shift Operations: SLL (Shift Left Logical), SRL (Shift Right Logical)

Control Signals

BR_EN: Branch Enable flag for conditional branches.

EX_MEM_COND: Determines whether a branch should be taken.

Open your terminal and type the following to install iverilog and GTKWave

$   sudo apt get update
$   sudo apt get install iverilog gtkwave

To clone the repository and download the netlist files for simulation , enter the following commands in your terminal.
$ git clone https://github.com/vinayrayapati/iiitb_rv32i
$ cd iiitb_rv32i

To simulate and run the verilog code , enter the following commands in your terminal.
$ iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
$ ./iiitb_rv32i

To see the output waveform in gtkwave, enter the following commands in your terminal.
$ gtkwave iiitb_rv32i.vcd


Task 5: Documentation and Repository Update :-
Overview: Object Detector Using Ultrasonic Sensor with CH32V003
Project Summary:
This project is designed to detect objects using an HC-SR04 ultrasonic sensor interfaced with a CH32V003 RISC-V microcontroller. When an object is detected within a certain range, an LED indicator lights up to provide a visual alert. The system operates using a 3.3V power supply and is built on a breadboard using jumper wires for easy prototyping.

Applications:
Obstacle Detection for Robots
Proximity Sensing in Security Systems
Smart Parking Systems
Automatic Door Systems

Hardware Components:
CH32V003 RISC-V Microcontroller (Processes sensor data)
HC-SR04 Ultrasonic Sensor (Measures distance)
LED (Indicates object detection)
3.3V Power Supply (Powers the circuit)
Breadboard & Jumper Wires (For easy wiring)
![ADD](https://github.com/user-attachments/assets/efcc1cff-5ec3-45ca-bef5-9353fa06aee9)
![ADDI](https://github.com/user-attachments/assets/ed842272-29d9-4d59-98f7-6a89f9d84d38)
![ADDI](https://github.com/user-attachments/assets/c425db9e-54b7-4946-8a10-21e1b83e05cf)
![AND](https://github.com/user-attachments/assets/867060a3-f2d3-4cc4-9a34-a1cac6abc211)
![AND](https://github.com/user-attachments/assets/6b1d16ab-b0c6-4e85-b07b-bb616062372d)
![BEQ](https://github.com/user-attachments/assets/9d882bad-7eed-437f-9554-70767c9d349e)
![FULL 5 STAGE](https://github.com/user-attachments/assets/7b872074-95e2-4397-bf6d-8f5362369700)
![LW](https://github.com/user-attachments/assets/20fa0712-863e-40fb-b232-e2007d04b2c1)
![OR](https://github.com/user-attachments/assets/2e8ab2c2-347a-4b74-bae3-8488f97bbe57)

Task 5:- : Documentation and Repository Update (Deadline: 28th January, 2025)
• Recording: Task 5 Recording.
• Update Repository:
o Add the Project Name and a brief Overview of your application.
o List Components Required to build your application.
Project Name:- WaveSense: Ultrasonic Range Finder

Overview: Object Detector Using Ultrasonic Sensor with CH32V003
Project Summary:
This project is designed to detect objects using an HC-SR04 ultrasonic sensor interfaced with a CH32V003 RISC-V microcontroller. When an object is detected within a certain range, an LED indicator lights up to provide a visual alert. The system operates using a 3.3V power supply and is built on a breadboard using jumper wires for easy prototyping.

Project Description
This project implements an object detection system using the HC-SR04 ultrasonic sensor and the CH32V003 RISC-V microcontroller. It measures the distance of objects and triggers an LED when an object is detected within a specified range. The system operates on a 3.3V power supply and is built using a breadboard for easy prototyping.

Working Principle
The ultrasonic sensor (HC-SR04) emits sound waves from its TRIG pin.
The waves bounce back when they hit an object and are received by the ECHO pin.
The CH32V003 microcontroller calculates the distance based on the time delay between transmission and reception.
If the object is closer than 10 cm, the LED turns ON. Otherwise, it remains OFF.

Table
![RACHU1](https://github.com/user-attachments/assets/9ec7ed06-1348-4a35-8e3f-174af586335b)

Components Required
![RACHU3](https://github.com/user-attachments/assets/24143aa3-991c-43fc-87b6-b66f98ff1df4)

![RACHU2](https://github.com/user-attachments/assets/678fd98c-5962-4fa9-a9c5-62e4bdd55356)

Task 6:- : Final Code Submission & Application Demo


![breadboard](https://github.com/user-attachments/assets/5ad7cd53-ee42-4cef-adc9-4844867323de)


























