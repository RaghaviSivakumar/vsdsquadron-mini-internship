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

#### I-TYPE
The upper 12 bits of I-type is an immediate number. The opcode is different from other instruction formats because the corresponding specific operations are different, and other parts are very similar to R-type.

#### S-TYPE
The characteristic of S-type instruction is that there is no rd register. In this type of instruction, the immediate is divided into two parts, the first part is in bit11-5, and the second part is in bit4-0. The 5 bits of the immediate 4-0 occupy the position of rd in other instruction formats, and 5-11 occupy the position of funct7. Explain that the command format does not need to write back. That is, read the two values from the two registers and perform the operation together with the immediate, and write the result to the register after the operation is over.

#### U-TYPE
A 20-bit immediate is provided in the U-type instruction. The final operation result is related to the 20-bit immediate, and the result is written back to the rd register. The opcode determines the type of operation. There are no funct3, rs1, rs2, and funct7 in U-type. This type of instruction structure is very simple.

#### B-TYPE
B-type instructions are mainly used as branch instructions, but they are conditional Branch. It means to decide whether to jump or not need to depend on whether the condition is valid. The B-type machine code structure is shown in Figure 2-1. The instruction does not include rd register and funct7, but contains rs1, rs2, funct3 and immediate. The immediate is divided into two areas. The encoding of B-type instruction immediate is out of order. The reason is not described in detail here. There is a specific article on the official site explaining why it is out of order. In short, it has been verified that the effect on CPU operation function when the immediate number sequence is in this order is very well. But the immediate is disrupted, so it will be decoded when the CPU executes in the future. After decoding, the CPU needs to restore the disrupted immediate in order. For example, when the CPU gets a B-type instruction, the immediate in it is scrambled, and the CPU needs to arrange the immediate in the order of 12-1 to restore the immediate.

#### J-TYPE
The format of this instruction is very similar to U-type, it only have Rd register and immediate and opcode. At the same time, the immediate of J-type is also disrupted. That means that the CPU must first put the immediate numbers together to restore the original immediate numbers when decoding.

</details>



  
  



  






