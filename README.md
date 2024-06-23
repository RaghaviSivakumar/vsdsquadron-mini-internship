# Vsdsquadron-mini-internship
The VSDSquadron Mini is a tiny RISC-V development board. It features a 32-bit RISC-V core, multiple clock options, 15 GPIO pins, and various communication ports like SPI and I2C.
## FEATURES
* Processor: 32-bit RISC-V core (RV32EC instruction set)
* Clock: Built-in 24MHz RC oscillator (x2 options), external oscillator slot
* Memory: 2KB SRAM, 16KB Flash.
* I/O: 15 GPIO pins
* Communication Interface: USART, I2C, SPI
## TASK 1
To install the RISC-V toolchain using VDI, write a C code to calculate the sum of numbers from 1 to N and analyse the risc assembly code.
### 1. Installation of the virtual box
![Virtual box installation](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/c766acf2-a5df-48ba-ab58-deda02cb8969)
### 2. Installation of Ubuntu
![Installation of Ubuntu](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/103c1e1c-9dc6-4b75-b9e4-9ac2fb3240a3)
### 3. C code to execute the sum of numbers from 1 to N
* Leafpad is installed using the command
  `sudo snap install leafpad`
* Creating the file using the command `leafpad sum1ton.c &`
* Write the C program.

![C program of sum of num from 1 to n](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d9d41ff6-667c-4f76-9e72-77ecde57a10c)
### 4. Output of the C program
* Compile the program using the command **gcc sum1ton.c** and execute the program using the command **./a.out**

![Output of the c program](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/bd30357f-4ff8-4ab4-880f-74b4af1c871a)
### 5. Converting the C program to RISC-V instruction set
* Using the command riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
* Also, to observe the difference executing the same with -Ofast instead of -O1 as **riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c** 

![fast instruction](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/211a916e-4934-41b2-b58e-c13a90f571cb)
### 6. Calculation of RISC-V instructions.
* Number of instructions are calculated,

![Calculation of riscv instructions](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/4da1e45a-c5c0-4319-b489-2c83a2125c60)




