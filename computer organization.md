COMPUTER ORGANIZATION

\[MODULE 1\]

INTRODUCTION

A computer as we know of is comprised of the main source of processing called the CPU (Central Processing Unit) which houses the motherboard. The motherboard is a large PCB (Printed Circuit Board) chunk that contains circuit maps and routings to various system components, such as memory, storage, processor, etc…

Abbreving to a computer can infer 5 fundamental units that account for the overall functioning :

**1. Input Unit:- **This unit is responsible for handling information entry/substitution by the user for a particular namespace or a mapping area. It acts as a server interface between the user itself and the system’s translating media to fetch the data in the order it’s intended to.

2. Memory Unit:- This unit is accountable for managing the entered input data for further analysis/processing and real-time assessment. Memory Unit essentially constitutes of two types – Volatile & Non-volatile. Volatile memories are those that usually make use of capacitors to hold data by reference of indexes as long as they’re powered up. When the power input is removed, the data is permanently lost. Volatile memory units have extremely fast throughputs because they work over pulses. Example – RAM. Non-volatile memory units on the other hand are those on which once the data is written, stays permanently irrespective of being powered off post writing. They’re comparatively slower (evolving now) than volatile (primary) memory modules, but fast enough to balance the throughput latency for the flow of data between the volatile and non-volatile memory junction. Example – SSD, HDD, etc.

3. Arithmetic & Logic Unit:- This is a part of the processor responsible for handling controlled execution of arithmetic and logical operations as instructed. It receives electrical impulses which are mapped by the processor to fetch input from specific entry points from the memory, and operate on that based on the hex or binary or asm instruction set.

**4. Output Unit:- **This unit handles the process of parsing the calculated output from the system memory to human understandable format by reading from input media in the form of electrical pulses and similar approaches to show it to the user.

5. Control Unit:- It’s the most viable component balancing the entire workflow of the system. It uses controlled flow of simulated impulses to instruct all the aforementioned units what to do next. For example, it sends a balanced beam of impulses to ALU to instruct it to fetch random memory from an entry point \\x84\\x53\\xff0\\x01 and then perform a particular operation on it.

BASIC OPERATIONAL CONCEPTS

The entire computer works on the principle of flow of instructions. Every set of work is processed as impulses in periodic recursion called clock cycles. It is measured in Hertz or it’s higher units. The higher the clock cycle represents the faster the processing power of CPU. All these instructions are entered by the user in a very human readable format, which is then compiled/interpreted to a low level language which is usually a binary code set or in some cases, another type of code that runs over a VM (Virtual Machine). For example, java natively runs over JVM (Java Virtual Machine) in the bytecode form, while android runs over the dalvik VM with ART (Android Runtime). All these in some way perform at a very low level language which makes it very fast for the cpu to process the instructions.

System Architecture:- The ISA (Instruction Set Architecture) also called as system architecture is the model for a particularly programmed silicon die block which states how the die acts for a particular impulse or an which is then coded as firmware in the form of instructions using hardware languages. The capability of a processor to handle a specific count of instructions is called IPS (Instructions Per Second). Example: arm, RISC, CISC, MIPS, etc. Together, it makes it the microprocessor.

**Assembly:- **In computer organization, any low-level language interfacing from instruction sets to the system architecture’s machine code is called an assembler (asm). There are many types of assemblers, for RISC, CISC, VLIW, DSP, etc.

To make things simpler, let’s take a basic example to see how things work at the low level (not diving too deep into assemblers) :

.data

var: .out 3

.text

global \_start

\_start:

ldr r0, adr\_var

ldr r1, \[r0\]

str r1, \[r0\]

What this line of code did is very simple – yet looks so different. Let’s start line by line interpretation of what exactly happens

.datacreates a section in the memory (at an unpredictable memory location) dynamically

var: .out 3creates a variable in that memory section and stores a value to it

.textmarks the beginning of the code where we start substituting instructions

global \_startglobal is a NASM specific directive (works essentially with Netwide Assembly over 16,32, and 64 bit microprocessors) \_start is a symbol (user-provided) which marks the beginning of execution of instructions in the object code. If global directive is missing, the symbol along with it’s section won’t be imported to the object code, so the linker wouldn’t know what to process. Linker and loader entry points can also be provided during parsing asm to object code. In a linux system, the basic conversion is done by a utility called **ld** which is called GNU linker. By default, it doesn’t recognizes a symbol other than \_start. So, if you explicitly want to replace the entry point with something else, you can flag **ld -e &lt;entry\_point&gt; -o obj**

\_start:It begins the label for the instructions section

ldr r0, adr\_varloads the memory address of the variable **var** into r0 register with the label/tag **adr\_var**

****

ldr r1, \[r0\]loads the value at memory address found in r0 to the register r1

str r1, \[r0\]stores the value found in r1 to the memory address of register r0

So, here what we did was take a value from the memory, load it’s memory address in the register r0, load the value at memory address stored in register r0 to r1 register, and stored the value r1 back to the memory address stored in register r0.

PS – This whole code is examplained for NASM (Netwide Assembler)

Similarly, depending on assemblers, it could change to LOAD, or similar.

REGISTERS

In computer architecture, a processor register is an extremely fast storage location which consists of a small memory to store specific hw instructions pre/post operation.

Let’s go over some basic registers in a computer system :

IR: The Instruction Register or IR holds the instruction that is currently being executed. It can be accessed by the control unit to validate threshold and manage time to push control signals to other process elements implemented.

PC: Program Counter or PC manages the instructions loaded in memory uniformly and parses them to keep track of which instruction is currently being executed and what shall the next instruction be. Depending on ISA, the program counter is incremented by 1 for 8-bit, 2 for 16-bit and 4 for 32-bit system and so on.

SP: Stack Pointer or SP records the address of last instruction sets unit (usually subroutines) request in stack format and the memory address of the top of stack (also called activation point), and in thread mode is used to balance pop or push of instruction elements

AC: Accumulator or AC for short is a unit type register used in several microprocessors which acts as an intermediate for storing and re-loading data values in between operations, and is usually used by ALU

MAR: MAR or Memory Address Register manages flow of data from the primary memory to the processor. It holds the memory address to/from which the data is to be transferred

MDR: MDR or Memory Data Register also manages flow of data form the primary memory to the processor. It however holds the actual data value instead of memory address which is to be read from/written to the primary memory.
