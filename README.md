# ASIC Design Project

# Task 1: Compiling the C code in GCC. Sum of numbers from 1 to 100 is calculated.
## Input
![Code1](https://github.com/user-attachments/assets/2639d3fa-5d2c-44f5-a0ba-e357e939eb47)
## Output
![Output1](https://github.com/user-attachments/assets/736f211b-c923-4118-85e3-9765bf240517)

## Result
Sum of numbers from 1 to 100 is 5050.



# Task 2 : RISC-V Compilation of a simple C Program

## Compilation using O1 switch
![O1 Output](https://github.com/user-attachments/assets/8999e17f-449f-439e-a749-fb571a838f7c)

## Compilation using Ofast switch
![OFast Output](https://github.com/user-attachments/assets/c8657ebb-1180-478a-b5b0-8d7e010c96af)

## Observation
From the above images we can observe that Ofast reduces the number of instruction to 12 compared to 15 in O1 switch.

# Task 3 : Spike Simulation and observation of RISC-V Objdump

## Objdump using RISC-V

![Output](https://github.com/user-attachments/assets/30feb5b9-23f2-4ce6-9174-d0b26231e47a)

## Debugging using Spike compiler

![Debugging](https://github.com/user-attachments/assets/306093aa-53df-4385-b699-d3c04d24bbc6)


## Calculations

![Calculation](https://github.com/user-attachments/assets/e198fe7e-5e00-4b90-8e89-fcb8877a31e6)

- Stack pointer gets updated by -16 in decimal which is -10 in hexadecimal so 0x0000003ffffffb50 gets updated to 0x0000003ffffffb40

# Task 4 :  RISC-V Instruction Encodings

32-bit binary  encodings for a set of RISC-V instructions is calculated. The encodings cover various types of instructions, including arithmetic, logical, immediate, store, load, and branch operations.

## Instruction Types

RISC-V instructions are categorized into several types, each with its own format:

1. **R-type**: Register-based operations.
   - Format: `[31:25] funct7 | [24:20] rs2 | [19:15] rs1 | [14:12] funct3 | [11:7] rd | [6:0] opcode`

2. **I-type**: Immediate operations, loads, and some branches.
   - Format: `[31:20] imm[11:0] | [19:15] rs1 | [14:12] funct3 | [11:7] rd | [6:0] opcode`

3. **S-type**: Store operations.
   - Format: `[31:25] imm[11:5] | [24:20] rs2 | [19:15] rs1 | [14:12] funct3 | [11:7] imm[4:0] | [6:0] opcode`

4. **B-type**: Branch operations.
   - Format: `[31:31] imm[12] | [30:25] imm[10:5] | [24:21] rs2 | [20:16] rs1 | [15:12] funct3 | [11:8] imm[4:1] | [7:0] imm[11] | [6:0] opcode`

5. **U-type**: Upper immediate operations.
   - Format: `[31:12] imm[31:12] | [11:7] rd | [6:0] opcode`

6. **J-type**: Jump operations.
   - Format: `[31:31] imm[19] | [30:21] imm[10:1] | [20:20] imm[11] | [19:12] imm[18:12] | [11:7] rd | [6:0] opcode`

## 32-bit Binary 

Below is a list of RISC-V instructions with their 32-bit binary 

### R-type Instructions
- **ADD r10, r11, r12**
  - **Binary**: `0000000 01100 01011 000 01010 0110011`
  

- **SUB r12, r10, r11**
  - **Binary**: `0100000 01010 01011 000 01100 0110011`
  

- **AND r11, r10, r12**
  - **Binary**: `0000000 01100 01010 111 01011 0110011`
  

- **OR r8, r11, r5**
  - **Binary**: `0000000 00101 01011 110 01000 0110011`
 

- **XOR r8, r10, r4**
  - **Binary**: `0000000 00100 01010 100 01000 0110011`
  

- **SLT r00, r1, r4**
  - **Binary**: `0000000 00100 00001 010 00000 0110011`
  

- **SLL r05, r01, r1**
  - **Binary**: `0000000 00001 00001 001 00101 0110011`
 

### I-type Instructions
- **ADDI r02, r2, 5**
  - **Binary**: `000000000101 00010 000 00010 0010011`
 

- **LW r03, r01, 2**
  - **Binary**: `000000000010 00001 010 00011 0000011`
  

### S-type Instructions
- **SW r2, r0, 4**
  - **Binary**: `0000000 00000 00010 010 00000 0100011`
  

### B-type Instructions
- **BNE r0, r0, 20**
  - **Binary**: `0000000 00000 00000 001 0100 1100011`


  

- **BEQ r0, r0, 15**
  - **Binary**: `0000000 00000 00000 000 1111 1100011`
 

### R-type Instructions with Shifts
- **SRL r06, r01, r1**
  - **Binary**: `0000000 00001 00001 101 00110 0110011`

# Task 5 : By making use of RISCV Core: Verilog Netlist and Testbench, perform an experiment of Functional Simulation and observe the waveforms
### Steps to perform functional simulation of RISCV  
1. Create a new directory with your name ```mkdir <your_name>```
2. Create two files by using ```touch``` command as ```bibin_rv32i.v``` and ```bibin_rv32i_tb.v```  
 
3. To run and simulate the verilog code, enter the following command:  
	```
	$ iverilog -o bibin_rv32i bibin_rv32i.v bibin_rv32i_tb.v
	$ ./bibin_rv32i
	```
5. To see the simulation waveform in GTKWave, enter the following command:
	```
	$ gtkwave bibin.vcd
	```


6. The GTKWave will be opened and following window will be appeared
![Opening](https://github.com/user-attachments/assets/dfd71184-5afd-4321-aab6-64a0c3e32667)

7. All the instructions are hardcoaded
 ![Hardcoded](https://github.com/user-attachments/assets/6d2b07f5-1dbf-43a0-b294-9b8187cb94c0)

8. Following are the differences between standard RISCV ISA and Hardcoded ISA:  
 

|  **Operation**  |  **Standard RISCV ISA**  |  **Hardcoded ISA**  |  
|  :----:  |  :----:  |  :----:  |  
|  ADD R6, R2, R1  |  32'h00110333  |  32'h02208300  |  
|  SUB R7, R1, R2  |  32'h402083b3  |  32'h02209380  |  
|  AND R8, R1, R3  |  32'h0030f433  |  32'h0230a400  |  
|  OR R9, R2, R5  |  32'h005164b3  |  32'h02513480  |  
|  XOR R10, R1, R4  |  32'h0040c533  |  32'h0240c500  |  
|  SLT R1, R2, R4  |  32'h0045a0b3  |  32'h02415580  |  
|  ADDI R12, R4, 5  |  32'h004120b3  |  32'h00520600  |  
|  BEQ R0, R0, 15  |  32'h00000f63  |  32'h00f00002  |  
|  SW R3, R1, 2  |  32'h0030a123  |  32'h00209181  |  
|  LW R13, R1, 2  |  32'h0020a683  |  32'h00208681  |  
|  SRL R16, R14, R2  |  32'h0030a123  |  32'h00271803  |
|  SLL R15, R1, R2  |  32'h002097b3  |  32'h00208783  |   

8. Analysing the Output Waveform of various instructions


 i) Add R6,R2,R1
 ![Add instruction](https://github.com/user-attachments/assets/bde13c2f-82c7-42c5-99df-8b1d166ffa1f)
Output: 1+2=3

ii) Sub R7,R1,R2 
![Subtraction Instruction](https://github.com/user-attachments/assets/820bf0cb-9803-4148-9a54-bad9d5fab48a)
Output: 1-2=-1

iii) AND R8,R1,R3
![And Instruction](https://github.com/user-attachments/assets/5d48f574-79f3-4529-bf6a-68e47f23325c)
Output: 3&1=1

iv) OR R9,R2,R5
![OR instruction](https://github.com/user-attachments/assets/e10375f6-7c4c-487b-8f10-28921745ff25)
Output: 2|5=7

v) XOR R10,R1,R4
![XOR Instruction](https://github.com/user-attachments/assets/dfa2601d-e2c1-427d-a990-45f7ce6072ef)

Output: 1^4=5

vi) SLT R1,R2,R4
![SLT Instruction](https://github.com/user-attachments/assets/faafcadd-d4af-4b20-b33c-3691f2888b35)
Output: Since 2<4 output is 1

vii) ADD1 R12,R4,5
![AddImmediate instruction](https://github.com/user-attachments/assets/e3348844-2a04-4192-b993-793354fce6a1)
Output : 4+5=9

viii) BEQ R0,R0,15
![BEQ Instruction](https://github.com/user-attachments/assets/00c33b1a-46b2-4482-a778-f8517a4b5248)
Output : Since value stored in both registers are same PC=PC+15=25

ix) SLL R15,R1,R2
![SLL Instruction](https://github.com/user-attachments/assets/39e698cc-c217-48b1-82a1-046d9192a563)
Output : (0001)<<2 = 0100 = 4 in decimal

# Task 6 : Capacitor Charging Application compilation using GCC and RISC-V GCC

### 1. **Code Snippet:**
 ```c
#include <stdio.h>
#include <math.h>

// Function to simulate capacitor charging
void simulate_capacitor_charging(double R, double C, double V_max, double time_step, double total_time) {
    double t = 0.0;
    double V = 0.0;

    printf("Time(s)\t\tVoltage(V)\n");
    printf("-----------------------------\n");

    while (t <= total_time) {
        V = V_max * (1 - exp(-t / (R * C)));
        printf("%.2f\t\t%.2f\n", t, V);
        t += time_step;
    }
}

int main() {
    double R, C, V_max, time_step, total_time;

    // Input parameters for the simulation
    printf("Enter the resistance (R) in ohms: ");
    scanf("%lf", &R);
    printf("Enter the capacitance (C) in farads: ");
    scanf("%lf", &C);
    printf("Enter the supply voltage (V_max) in volts: ");
    scanf("%lf", &V_max);
    printf("Enter the time step for the simulation (in seconds): ");
    scanf("%lf", &time_step);
    printf("Enter the total time for the simulation (in seconds): ");
    scanf("%lf", &total_time);

    // Simulate capacitor charging
    simulate_capacitor_charging(R, C, V_max, time_step, total_time);

    return 0;
}
```

### 2. **Compilation of the code with GCC Compiler**

![C code](https://github.com/user-attachments/assets/4c1df86c-5435-40b7-849b-e481bce8b2f9)

### 3. **Compilation of the code using RISC-V GCC Compiler**


![Riscv output](https://github.com/user-attachments/assets/159232ec-2d01-412a-b6f3-5e2241aa5b27)

## Result

### The output received after both GCC Compilation and Risc-V GCC Compilation are same.

# Task 7 : 5-Stage Pipelined RISC-V Processor

Here we are going to design a simple RISC-V Core CPU as per the below diagram.

![RISC-V Core Architecture](https://github.com/user-attachments/assets/458c4d1a-9ac3-490c-baa2-bb766ea122ed)

##  1) Program Counter 

![Program Counter Full](https://github.com/user-attachments/assets/f7587da7-ffc3-435a-9dbc-e90de64b2fa8)

## 2) Instruction Fetch

![Instruction Fetch](https://github.com/user-attachments/assets/ebc8a122-6c61-4c62-83bb-bd3e02b465ce)

## 3) Instruction Decode

![Decode](https://github.com/user-attachments/assets/bc66588f-f169-490c-b0ef-5c87c031f5cd)

## 4) Register File Read

![Register Read](https://github.com/user-attachments/assets/8cb6eb2e-6fbb-4a38-b3b3-b2783f025a85)

## 5) ALU

![ALU](https://github.com/user-attachments/assets/23a990ce-da7d-4d0c-953b-0fc65a926c13)

## 6) Register file write

![Register Write](https://github.com/user-attachments/assets/a853b4ec-cba5-4d53-badb-5b177321a8eb)

## 7) Branching

![Branching](https://github.com/user-attachments/assets/4b464a4f-6cde-4525-b827-3e9b8619ff3c)

## 8) Testbench
![Testbench](https://github.com/user-attachments/assets/289ac6cf-853b-4dde-94fd-155aa3f0bcb1)

### Result : RISC-V Core CPU is implemented

## 9) Pipelining the CPU


![Valid Pipeline](https://github.com/user-attachments/assets/2f8498c2-bd5c-4b1a-8d64-01a4f6ae0418)

![Validating Code](https://github.com/user-attachments/assets/8e29cebb-80af-4d85-b3b5-f578f0d9b6aa)

## 10) 5-Stage Pipelined RISC-V Processor

![Pipelined RISC-V](https://github.com/user-attachments/assets/86e0e6b0-dfb4-4407-b202-494158e9c92b)

![Pipelined Risc-V Architecture](https://github.com/user-attachments/assets/52d6daba-faa7-47f1-9528-2623c7ae407a)

![Final sum](https://github.com/user-attachments/assets/74a94aa2-9ed1-4c7d-aba3-6520a34ae1c9)

### Result : Final waveform showing the sum of first 1 to 9 numbers as 2D in hex format
















