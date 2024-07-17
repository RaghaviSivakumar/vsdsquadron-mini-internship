# Vsdsquadron-mini-internship
The VSDSquadron Mini is a tiny RISC-V development board. It features a 32-bit RISC-V core, multiple clock options, 15 GPIO pins, and various communication ports like SPI and I2C.
## FEATURES
* Processor: 32-bit RISC-V core (RV32EC instruction set)
* Clock: Built-in 24MHz RC oscillator (x2 options), external oscillator slot
* Memory: 2KB SRAM, 16KB Flash.
* I/O: 15 GPIO pins
* Communication Interface: USART, I2C, SPI
 <details>
<summary>TASK 1</summary>
<br>   
  
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
* Compile the program using the command `gcc sum1ton.c` and execute the program using the command `./a.out`

![Output of the c program](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/bd30357f-4ff8-4ab4-880f-74b4af1c871a)
### 5. Converting the C program to RISC-V instruction set
* Using the command `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c`
* In another tab, use the following command to visualize the assembly code `riscv64-unknown-elf-objdump -d sum1ton.o| less` and to access the main part use command `/main`
* Also, to observe the difference executing the same with -Ofast instead of -O1 as `riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c` 

![fast instruction](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/211a916e-4934-41b2-b58e-c13a90f571cb)
### 6. Calculation of RISC-V instructions.
* Number of instructions are calculated,

![Calculation of riscv instructions](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/4da1e45a-c5c0-4319-b489-2c83a2125c60)
</details>

<details>
<summary>TASK 2</summary>
 <br>
 
## SMART ELEVATOR CONTROLLER
A smart elevator controller is designed to optimize the operation of an elevator system using advanced algorithms and modern technology. It reduces wait times, improves energy efficiency, and enhances the user experience by dynamically responding to varying demand patterns. Key features may include load sensors, position sensors, occupancy sensors, and intelligent dispatch systems.

## 1. C code for the elevator controller
* Creating the file using the command `leafpad elevator.c &`
* The sample C code for the smart elevator controller can be given as

```
#include <stdio.h>
#include <stdbool.h>

#define NUM_FLOORS 10
#define NUM_ELEVATORS 1

// Elevator states
typedef enum {
    IDLE,
    MOVING_UP,
    MOVING_DOWN,
    DOOR_OPEN,
    DOOR_CLOSED
} ElevatorState;

// Elevator struct
typedef struct {
    int currentFloor;
    ElevatorState state;
} Elevator;

// Function prototypes
void initializeElevator(Elevator *elevator);
void moveElevator(Elevator *elevator, int targetFloor);
void openDoor(Elevator *elevator);
void closeDoor(Elevator *elevator);

int main() {
    Elevator elevators[NUM_ELEVATORS];
    int targetFloor;

    // Initialize elevator(s)
    for (int i = 0; i < NUM_ELEVATORS; i++) {
        initializeElevator(&elevators[i]);
    }

    // Example scenario: Request to go to floor 5
    targetFloor = 5;

    // Assuming there's only one elevator in this example
    moveElevator(&elevators[0], targetFloor);

    return 0;
}

void initializeElevator(Elevator *elevator) {
    elevator->currentFloor = 1;  // Start at floor 1
    elevator->state = IDLE;
}

void moveElevator(Elevator *elevator, int targetFloor) {
    if (elevator->currentFloor < targetFloor) {
        elevator->state = MOVING_UP;
        printf("Elevator moving up...\n");
        while (elevator->currentFloor < targetFloor) {
            elevator->currentFloor++;
            // Simulating movement delay
            printf("Floor %d\n", elevator->currentFloor);
        }
    } else if (elevator->currentFloor > targetFloor) {
        elevator->state = MOVING_DOWN;
        printf("Elevator moving down...\n");
        while (elevator->currentFloor > targetFloor) {
            elevator->currentFloor--;
            // Simulating movement delay
            printf("Floor %d\n", elevator->currentFloor);
        }
    }

    // Arrived at target floor
    elevator->state = DOOR_OPEN;
    openDoor(elevator);
    closeDoor(elevator);
}

void openDoor(Elevator *elevator) {
    elevator->state = DOOR_OPEN;
    printf("Elevator door opening...\n");
    // Simulating door opening delay
    printf("Door opened.\n");
}

void closeDoor(Elevator *elevator) {
    elevator->state = DOOR_CLOSED;
    // Simulating door closing delay
    printf("Elevator door closing...\n");
    printf("Door closed.\n");
}
```
![Program for smart elevator controller](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/253098db-5635-492f-a11e-700eeda5e477)
![Program for smart elevator controller1](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d2b5d337-63de-468e-b88a-6adbd3ebe2ae)
![Program for smart elevator controller2](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/b1fb67a0-c35a-4bbc-a6a0-66825a062381)
![Program for smart elevator controller3](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/f9774793-b667-4a22-b93d-206c9f59d5c4)

## 2. The output of the code
* Compile the program using the command `gcc elevator.c` and execute the program using the command `./a.out`

  ![The output of the code](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d0c2da82-4725-45ed-9bec-91e044447703)
  
## 3. Converting the C program to RISC-V instruction set
* Using the command `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o elevator.o elevator.c`
  
  ![RISC-V instructions(O1)-1](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/8f5c62e8-057d-4bb0-a8a5-21b9a9dbeb9a)


* In another tab, use the following command to visualize the assembly code `riscv64-unknown-elf-objdump -d elevator.o | less`

  ![To get the Output of the instruction](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/595efc05-d3a4-4eed-a042-4925d9fa136c)

  
* To access the main part use command `/main`

  ![Searching for the main part-command](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/b13fff4e-0685-4340-b41f-044e6d94e2a6)


* Number of instructions are calculated at `-O1`

  ![Screenshot 2024-06-25 010055](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/7fcf38a0-ba6e-4f0f-b072-e1462b733f4b)

  There are 12 lines of instructions in the main part of the code.


* To observe the difference executing the same with -Ofast instead of -O1 as `riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o elevator.o elevator.c`

  ![RISC-V instruction(Ofast)](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/153d84a0-c026-44a7-8840-33589eeba998)


* Similarly,accessing the main part and the number of instructions are being calculated at `-Ofast`

  ![Screenshot 2024-06-25 010356](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/54c71a41-d3c9-453d-bf7d-515aa9e96c80)

  There are 11 lines of instructions in the main block when executed at `-Ofast`
  By comparing, the number of instructions are reduced from 12 to 11 at `-Ofast`
  </details>
<details>
<summary>TASK 3</summary>
 <br>
  To execute the spike simulation of the previous project (Smart elevator controller),to observe with -O1 and -Ofast and to run the RISC-V instructions.

* Compiling the smart elevator controller program using the command `gcc sum1ton.c` and executing the same using the command `./a.out`.
* Also, executing the same code in RISC-V compiler by calling the program using the command `riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o elevator.o elevator.c` and executing using the spike command `spike pk elevator.o`
* We obtain the same output at both the cases.

![Output at both cases](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/fad9c6f4-1eb2-4913-bf9a-e7688829d5ac)


* To debug,Opening the objdump of the smart elevator controller code using the command `riscv64-unknown-elf-objdump -d elevator.o | less`

 ![less](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/da47034e-fe18-4e82-a37d-2444c4539738)
 
* Furtherly, to debug those instruction got from the objdump, we need to open a debuger and we will be debuggging the spike using the command `spike -d pk elevator.o`

![Debugger](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d2b6808f-f6b4-4fd9-aece-68a2ceb857d6)

* By using the command `until pc 0 100b0`, the program counter runs from 0 till the assembly code 100b0.

![until 100b0](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/16124c13-4793-4803-9773-82cec46b4bd7)

* To find the contents of a particular assembly code, use the command `reg 0 sp` and by pressing enter the next instruction will be executed.

![sp](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d8431af8-7e62-4dd4-838c-6c6955ab0a8d)

* By giving the `reg 0 sp` command again, we can find the updated value of the sp-stack pointer.
* Here, initially the value of sp was `0x0000003ffffffb50` at the next code, the sp is subtracted with the hexadecimal value of `32` which is `20`, furtherly after the execution of the code, the value of sp is updated as `0x0000003ffffffb30`(where addi-add immediate).
  
![Screenshot 2024-06-27 124102](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/e3b0a699-8a82-420d-bd64-be7495bd5324)
![Screenshot 2024-06-27 125953](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/0349f4cc-27d2-460d-b4a4-bc84bf897ae2)
</details>

<details>
<summary>TASK 4</summary>

### RISC-V Instruction Types
* R-type instructions for register-register operations
* I-type instructions for immediate and load operations
* S-type instructions for store operations
* B-type instructions for conditional branch operations
* U-type instructions for long immediate
* J-type instructions for unconditional jumps.

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/46c7bc3a-ef90-449b-862b-4250d94e3a50)

#### R-TYPE
The R-type command format is very clear. In the actual encoding process, the arrangement of encoding positions is meaningful. For example, the encoding position of the three register indexes in different instruction formats are always the same. Index of Rd is at 11-7, Index of rs1 is at 19-15, and Index of rs2 is at 24-20. This is their fixed position. Some instructions may not be useful. The index to the partial register. For example, there is no rs2 in the second instruction type I-type, but there are rs1 and rd and their indexes are in the corresponding positions. For another example, in s-type funct3 is at bits 14-12. The opcode is available in all instruction formats, and the position remains unchanged, always bit 0-6.

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/01d43f07-33cb-4d10-a363-b10659c9e282)


#### I-TYPE
The upper 12 bits of I-type is an immediate number. The opcode is different from other instruction formats because the corresponding specific operations are different, and other parts are very similar to R-type.

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/b861711c-2089-43f4-a58a-715bcbf7158d)
![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d7dc39a8-61fd-4652-9dc5-65a74052307f)



#### S-TYPE
The characteristic of S-type instruction is that there is no rd register. In this type of instruction, the immediate is divided into two parts, the first part is in bit11-5, and the second part is in bit4-0. The 5 bits of the immediate 4-0 occupy the position of rd in other instruction formats, and 5-11 occupy the position of funct7. Explain that the command format does not need to write back. That is, read the two values from the two registers and perform the operation together with the immediate, and write the result to the register after the operation is over.


#### U-TYPE
A 20-bit immediate is provided in the U-type instruction. The final operation result is related to the 20-bit immediate, and the result is written back to the rd register. The opcode determines the type of operation. There are no funct3, rs1, rs2, and funct7 in U-type. This type of instruction structure is very simple.

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/ed2f9f5a-824e-41b8-87b7-a10349118a08)


#### B-TYPE
B-type instructions are mainly used as branch instructions, but they are conditional Branch. It means to decide whether to jump or not need to depend on whether the condition is valid. The B-type machine code structure is shown in Figure 2-1. The instruction does not include rd register and funct7, but contains rs1, rs2, funct3 and immediate. The immediate is divided into two areas. The encoding of B-type instruction immediate is out of order. The reason is not described in detail here. There is a specific article on the official site explaining why it is out of order. In short, it has been verified that the effect on CPU operation function when the immediate number sequence is in this order is very well. But the immediate is disrupted, so it will be decoded when the CPU executes in the future. After decoding, the CPU needs to restore the disrupted immediate in order. For example, when the CPU gets a B-type instruction, the immediate in it is scrambled, and the CPU needs to arrange the immediate in the order of 12-1 to restore the immediate.

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/b463502a-6544-4791-834c-18b8bb14e5aa)


#### J-TYPE
The format of this instruction is very similar to U-type, it only have Rd register and immediate and opcode. At the same time, the immediate of J-type is also disrupted. That means that the CPU must first put the immediate numbers together to restore the original immediate numbers when decoding.

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/3b3f4428-09c7-4e03-a585-3f6e0cb94865)

### INSTRUCTIONS and 32 BIT MACHINE CODES


`1.ADD r1,r2,r3`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0000000
* rs2(r3)-00011
* rs1(r2)-00010
* funct3-000
* rd(r1)-00001
* opcode-0110011
```
*32-bit code:0000000 00011 00010 000 00001 0110011*

`2.SUB r3,r1,r2`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0100000
* rs2(r2)-00010
* rs1(r1)-00001
* funct3-000
* rd(r1)-00011
* opcode-0110011
```
*32-bit code:0100000 00010 00001 000 00011 0110011*

`3.AND r2,r1,r3`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0000000
* rs2(r3)-00011
* rs1(r1)-00001
* funct3-111
* rd(r2)-00010
* opcode-0110011
```
*32-bit code:0000000 00011 00001 111 00010 0110011*

`4.OR r8,r2,r5`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0000000
* rs2(r5)-00101
* rs1(r2)-00010
* funct3-110
* rd(r2)-01000
* opcode-0110011
```
*32-bit code:0000000 00101 00010 110 01000 0110011*

`5.XOR r8,r1,r4`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0000000
* rs2(r4)-00100
* rs1(r1)-00001
* funct3-100
* rd(r8)-01000
* opcode-0110011
```
*32-bit code:0000000 00100 00001 100 01000 0110011*

`6.SLT r10,r2,r4`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0000000
* rs2(r4)-00100
* rs1(r2)-00010
* funct3-010
* rd(r2)-01010
* opcode-0110011
```
*32-bit code:0000000 00100 00010 010 01010 0110011*

`7.ADDI r12,r3,5`
```
* Instruction-I-type
  According to the structure of I-type
* imm[11:0](5)-000000001001
* rs1(r3)-00011
* funct3-000
* rd(r12)-01100
* opcode-0010011
```
*32-bit code:000000001001 00011 000 01100 0010011*

`8.SW r3,r1,4`
```
* Instruction-S-type
  According to the structure of S-type
* imm[11:5]-0000000
* rs2(r3)-00011
* rs1(r1)-00001
* funct3-010
* imm[4:0]-00100
* opcode-0100011
```
*32-bit code:0000000 00011 00001 010 00100 0100011*

`9.SRL r16,r11,r2`
```
* Instruction-R-type
  According to the structure of R-type
* funct7(ADD)-0000000
* rs2(r2)-00010
* rs1(r11)-01011
* funct3-101
* rd(r2)-10000
* opcode-0110011
```
*32-bit code:0000000 00010 01011 101 10000 0110011*

`10.BNE r0,r1,20`
```
* Instruction-B-type
  According to the structure of B-type
* offset[12,10:5]-0000001
* rs2(r1)-00001
* rs1(r0)-00000
* funct3-001
* offset[11,4:1]-01000
* opcode-1100011
```
*32-bit code:0000001 00001 00000 001 01000 1100011*

`11.BEQ r0,r0,15`
```
* Instruction-B-type
  According to the structure of B-type
* offset[12,10:5]-0000000
* rs2(r0)-00000
* rs1(r0)-00000
* funct3-000
* offset[11,4:1]-11110
* opcode-1100011
```
*32-bit code:0000000 00000 00000 000 11110 1100011*

`12.LW r13,r11,2`
```
* Instruction-I-type
  According to the structure of I-type
* imm[11:0](2)-000000000010
* rs1(r11)-01011
* funct3-010
* rd(r13)-01101
* opcode-0000011
```
*32-bit code:000000000010 01011 010 01101 0000011*

`13.SLL r15,r11,r2`
```
* Instruction-R-type
  According to the structure of R-type
* funct7-0000000
* rs2(r2)-00010
* rs1(r11)-01011
* funct3-001
* rd(r15)-01111
* opcode-0110011
```
*32-bit code:0000000 00010 01011 001 01111 0110011*


</details>

<details>
 <summary>TASK 5</summary>
 <br>
 
## Using the RISC-V core verilog netlist and testbench for functional simulation experiment.To upload the waveform snapshots for the commands.
#### 1. Cloning the reference repo:
* By using the command `git clone https://github.com/vinayrayapati/rv32i.git proj name` ,clone the reference repo which contains the verilog netlist and testbench

![Screenshot from 2024-07-06 19-43-10](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/d9fe452e-3c7e-484c-a3a3-9a80780426c2)

#### 2. Installation to setup simulation tools:
* To setup the simulation tools such as iverilog and GTKwave, using the command
`sudo apt update` and
`sudo apt install iverilog gtkwave`

![Screenshot from 2024-07-06 20-03-20](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/4b68a768-d1b9-4fa6-a199-9d7e23e2d5e9)


#### 3. Edit the testbench file:
* Use the command `nano iiitb_rv32i_tb.v`
* Check the testbench format is as below.

![Screenshot from 2024-07-06 20-19-23](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/792d52f1-1682-4f94-93f1-1ce2476e0c9d)
![Screenshot from 2024-07-06 20-15-31](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/b98d1db0-088b-437a-b349-65174dbc8e85)

#### 4. Run the functional simulation:
* To compile and simulate use the commands `iverilog -o rv32i_simulation iiitb_rv32i_tb.v` and `vvp rv32i_simulation`

![Screenshot from 2024-07-06 20-26-02](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/8d8768c9-714f-4d7d-b07b-e1fc7a62ae15)

#### 5. View the waveform:
* To view the waveform,use the command  `gtkwave simulation.vcd`

![Screenshot from 2024-07-06 20-29-32](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/2c81f700-4406-4b6a-b8dc-b6a6fec5d4d2)

* If no directory found,use the command `gtkwave simulation.vcd`

![Screenshot from 2024-07-06 20-34-58](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/715dabc9-52cd-4b3f-b4e5-48807fdb2f1d)

Furtherly,the gtkwave window will open.

![Screenshot from 2024-07-06 20-31-38](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/89d20d15-158e-4b0f-8da6-7a59d2c8c442)

#### Output waveform:
* Add the signals from the list and append,furtherly the waveforms will appear.

##### 1.ADD:

![Screenshot from 2024-07-06 20-48-44](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/889d0045-cc34-446f-8914-1aab9cbec840)
##### 2.SUB:

![Screenshot from 2024-07-06 20-54-45](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/608ece20-8fa5-4e48-8ef1-6d37a02a2628)
##### 3.AND:

![Screenshot from 2024-07-06 20-57-14](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/91bda506-1537-4b4e-9e1f-bf5c26547871)
##### 4.OR:

![Screenshot from 2024-07-06 20-59-24](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/cc81e966-2a98-474e-aef2-5cf2bd060850)
##### 5.XOR:

![Screenshot from 2024-07-06 21-00-52](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/556a7e0d-cc87-4d48-9549-64e8d629e3cc)

##### 6.SLT:

![Screenshot from 2024-07-06 21-02-02](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/da48102b-5bf9-4044-b516-b80a14788beb)
##### 7.BEQ:

![Screenshot from 2024-07-06 21-03-06](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/4de4cf15-7e94-408d-a199-dac880acb1c5)

</details>

<details>
 <summary>TASK 6</summary>
 <br>

 # SMART ELEVATOR CONTROLLER
 ## OVERVIEW
The Smart Elevator Controller project leverages ultrasonic sensing technology, the CH32V003 RISC-V processor, a servo motor, a touch sensor, and an LED display to create an automated and user-friendly elevator control system. This system operates by detecting the presence and position of individuals within the elevator using an ultrasonic sensor, which sends signals to the CH32V003 RISC-V processor. Upon receiving these signals, the processor activates a servo motor to move the elevator to the appropriate floor, uses touch sensors to determine the current floor, and displays the floor number using LEDs. This setup ensures seamless, efficient, and safe operation of the elevator, enhancing user convenience and safety by eliminating the need for manual control.

 ## COMPONENTS REQUIRED
* CH32V003X
* Ultrasonic Sensor (HC-SR04)
* Servo Motor (e.g., MG90S)
* Touch Sensor
* LED Lights
* Resistors (appropriate values for LEDs)
* Breadboard
* Jumper Wires

   The CH32V003 RISC-V processor operates at voltages between 1.8V to 3.6V, featuring GPIO pins for interfacing with external devices and supporting communication protocols like SPI, I2C, and UART. The ultrasonic sensor typically operates at 5V, detecting the distance of objects by emitting and receiving ultrasonic waves and converting this information into electrical signals. The servo motor operates within a voltage range suitable for the load and torque requirements of the elevator and responds to control signals for precise movement. The touch sensor is used to detect which floor the elevator is currently at, and the LEDs are used to display the floor number.
 
   
 ## CIRCUIT CONNECTION FOR SMART ELEVATOR CONTROLLER
 In the Smart Elevator Controller project, the ultrasonic sensor is connected to the CH32V003 RISC-V processor as follows: The Trigger pin (TRIG) of the ultrasonic sensor, which initiates the ultrasonic pulse, is connected to the PC0 pin of the CH32V003 processor. The Echo pin (ECHO), which receives the reflected pulse and provides a signal indicating the distance, is connected to the PC1 pin of the processor. Additionally, the VCC (power) pin of the ultrasonic sensor is connected to the appropriate voltage supply pin (VCC) on the CH32V003, while the GND (ground) pin of the sensor is connected to the ground pin (GND) of the processor. This setup ensures that the CH32V003 can both send trigger signals and receive echo signals from the ultrasonic sensor, enabling it to detect objects and their distances.

Furthermore, the servo motor is connected to the CH32V003 processor as follows: The control pin of the servo motor is connected to the PD1 pin of the CH32V003 processor. Additionally, the VCC pin of the servo motor is connected to the appropriate voltage supply pin (VCC) on the processor, while the GND pin of the servo motor is connected to the ground pin (GND) of the processor.

The touch sensor is connected to the CH32V003 processor as follows: The output pin of the touch sensor is connected to the PD2 pin of the processor. Additionally, the VCC pin of the touch sensor is connected to the appropriate voltage supply pin (VCC) on the processor, while the GND pin of the touch sensor is connected to the ground pin (GND) of the processor. This setup ensures that the CH32V003 can receive signals from the touch sensor to determine the current floor.

The LED lights are connected to the CH32V003 processor as follows: The anode of each LED is connected to a separate GPIO pin (e.g., PC2, PC3, PC4, PC5) through appropriate current-limiting resistors. The cathode of each LED is connected to the ground pin (GND) of the processor. This setup allows the CH32V003 processor to control the LEDs and display the floor number.

## PINOUT DIAGRAM FOR SMART ELEVATOR CONTROLLER

![image](https://github.com/RaghaviSivakumar/vsdsquadron-mini-internship/assets/147801536/a837b81d-cc59-4981-b4ca-eba055834896)




## TABLE FOR PIN CONNECTION

#### 1.Ultrasonnic sensor to CH32V003x

|**Ultrasonic sensor**|**CH32V003x**|
| --- | --- |
| VCC | VIN |
| TRIG | PC0 |
|ECHO|PC1|
| GND | GND |

#### 2.Servo motor to CH32V003x

|**Servo motor** |**CH32V003x**|
|---|---|
| VCC                    | VIN           |
| Control                | PD1           |
| GND                    | GND           |

#### 3.Touch sensor to CH32V003x

| **Touch sensor** |**CH32V003x** |
|---|---|
| VCC                    | VIN           |
| Output                 | PD2           |
| GND                    | GND           |
#### 4. LED lights to CH32V003x
| **LED lights** |**CH32V003x**|
|---|---|
| LED1                   | PC2           |
| LED2                   | PC3           |
| GND                    | GND           |

* The anodes of the LED are connected to the GPIO pins.
* The cathodes are connected to the ground.

## CODE

C code for the smart elevator controller

```
#include <stdio.h>
#include <stdint.h>
#include "CH32V003.h" // Include the appropriate header file for the CH32V003 processor
#include "lcd.h"      // Include your LCD library header
#include "delay.h"    // Include a delay library for timing

// Pin definitions
#define TRIG_PIN    PC0
#define ECHO_PIN    PC1
#define SERVO_PIN   PD1
#define TOUCH_PIN   PD2
#define LED1_PIN    PC2
#define LED2_PIN    PC3

void GPIO_Init() {
    // Initialize GPIO pins for output/input
    // Setup TRIG_PIN, SERVO_PIN, LED1_PIN, LED2_PIN as outputs
    // Setup ECHO_PIN, TOUCH_PIN as inputs
    // You need to write specific code to initialize the GPIO pins as per your hardware setup
}

void Ultrasonic_Init() {
    // Initialize the ultrasonic sensor
    GPIO_Init();
}

uint32_t Ultrasonic_Read() {
    uint32_t duration, distance;

    // Trigger the ultrasonic sensor
    GPIO_WriteBit(TRIG_PIN, Bit_SET);
    delay_us(10); // 10 microseconds pulse
    GPIO_WriteBit(TRIG_PIN, Bit_RESET);

    // Measure the echo time
    while (GPIO_ReadInputDataBit(ECHO_PIN) == Bit_RESET); // Wait for the echo to start
    duration = 0;
    while (GPIO_ReadInputDataBit(ECHO_PIN) == Bit_SET) {
        duration++;
        delay_us(1);
    }

    // Calculate the distance in centimeters
    distance = (duration / 2) / 29.1;

    return distance;
}

void Servo_Init() {
    // Initialize the servo motor
    GPIO_Init();
}

void Servo_SetAngle(uint8_t angle) {
    // Set the servo motor to a specific angle
    // Convert angle to pulse width
    uint16_t pulse_width = 1000 + ((angle * 1000) / 180); // 1ms to 2ms pulse width for 0 to 180 degrees
    GPIO_WriteBit(SERVO_PIN, Bit_SET);
    delay_us(pulse_width);
    GPIO_WriteBit(SERVO_PIN, Bit_RESET);
    delay_us(20000 - pulse_width); // 20ms period - pulse width
}

void LED_DisplayFloor(uint8_t floor) {
    // Display the current floor using LEDs
    GPIO_WriteBit(LED1_PIN, (floor == 0) ? Bit_SET : Bit_RESET);
    GPIO_WriteBit(LED2_PIN, (floor == 1) ? Bit_SET : Bit_RESET);
}

uint8_t TouchSensor_Read() {
    // Read the current floor from the touch sensor
    if (GPIO_ReadInputDataBit(TOUCH_PIN) == Bit_SET) {
        return 1; // Assuming touch sensor indicates the first floor
    }
    return 0; // Assuming no touch indicates the ground floor
}

int main(void) {
    uint32_t distance;
    uint8_t current_floor = 0;

    // Initialize all components
    Ultrasonic_Init();
    Servo_Init();
    GPIO_Init();

    while (1) {
        // Read distance from the ultrasonic sensor
        distance = Ultrasonic_Read();

        // Determine the floor based on the distance
        if (distance < 10) {
            current_floor = TouchSensor_Read();
        }

        // Move the servo motor to the corresponding floor
        if (current_floor == 0) {
            Servo_SetAngle(0); // Move to ground floor
        } else if (current_floor == 1) {
            Servo_SetAngle(90); // Move to first floor
        }

        // Display the current floor using LEDs
        LED_DisplayFloor(current_floor);

        // Small delay before the next measurement
        delay_ms(500);
    }

    return 0;
}

```






 
</details>


<details>
 <summary>TASK 7</summary>
<br>

 # DEMONSTRATION OF THE PROJECT
 The demonstartion video of the smart elevator controller.
 
 https://drive.google.com/file/d/1FIdtm-Jhz8_5M5f1hPtYF7V6Ntli6cNO/view?usp=drive_link
</details>  
  



  






