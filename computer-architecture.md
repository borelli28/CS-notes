# UC Berkeley CS61C:  Great Ideas in Computer Architecture - [UC Berkeley CS 61C Great Ideas in Computer Architecture](https://www.youtube.com/playlist?list=PLhMnuBfGeCDM8pXLpqib90mDFJI-e1lpk)


### Lecture 1 - Intro
6 Great ideas in computer architecture:
1) Abstration(Layers of representation/interpretation):
    - Logic gates
    - ALU(e.g. Adder wth logic gates)
    - Machine language
    - Assembly language
    - High level language
2) Moore's Law(Designing through trends): Predicts 2X transistors / chip every 2 years.
3) Principle of locality(Memory hierarchy): How far away is the data?
4) Parallelism
5) Performance measurement & improvement
6) Dependability via redundancy: Redundancy so that a failing piece doesn't make the whole system fail.

Inside computers, everything is a number.

### Lecture 2 - Introduction to C, Part 1
C Compilers: Map C programs into machine code(binary).

C Pre Processor(CPP): 
- C source files pass through CPP before the compiler.
- CPP replaces comments with single space.
- Insert header files(stdio.h).

Storage: Manual(**malloc**, **free**)

When a C program starts:
- C executable a.out is loaded into memory by the OS.
- OS sets up the stack, then calls the C runtime library.
- Runtime first initialize memory and other libraries.
- Runtime calls main().

Pointer: A variable that contains the address of a memory location for a variable.
