

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

# Task 8 : Conversion from TLV into Verilog using Sandpiper-SaaS compiler.


1. **Install Required Packages:**
Begin by installing the necessary packages using pip:
```bash
pip3 install pyyaml click sandpiper-saas
```
2. **Clone the github repo:** 
clone this repo containing VSDBabySoC design files and testbench. Move into the VSDBabySoc directory
```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoc
```

3. **Replace the rvmyth.tlv file in the VSDBabySoC Directory:** 
replace in src/module with the rvmth.tlv.

4. **Convert .tlv to .v using converter:**
Now we have written the code in TL-Verilog .tlv which is a high level language and we want to convert into low level verilog that is to translate .tlv definition of rvmyth into .v definition. To do so Run the following command as follows

```bash
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```

5. **Make the pre_synth_sim.vcd:**
We will create the pre_synth_sim.vcd by running the following command
```bash
make pre_synth_sim
```
The result of the simulation i.e the pre_synth_sim.vcd will be stored in the output/pre_synth_sim directory


6 .**Now to compile and simulate RISC-V design run the following code:**
To compile and simulate vsdbabysoc design.

```bash
iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module
cd output
./pre_synth_sim.out
```
To generate pre_synth_sim.vcd file,which is our simulation waveform file.


7. **To open the Simulation file in gtkwave tool:**
To do so run the follwowing command 
```bash
gtkwave pre_synth_sim.vcd
```
![GTK Code](https://github.com/user-attachments/assets/971dfc55-3d5d-417e-ad11-802aa7b99f79)

### Verilog Waveform
![GTKWave Output](https://github.com/user-attachments/assets/897a01fd-aab4-42a3-b7f1-7b85885d7a98)

### Comparison with TL Verilog Waveform
![Final sum](https://github.com/user-attachments/assets/74a94aa2-9ed1-4c7d-aba3-6520a34ae1c9)

### Result : Final waveform showing the sum of first 1 to 9 numbers as 2D in hex format is same for Verilog and TL Verilog.


# Task 9 : BabySoc Simulation

## Two IPs PLL and DAC are added to RISC-V Core

### i) Phase-Locked Loop
Phase-Locked Loop (PLL) is a control system that generates an output signal whose phase is related to the phase of an input signal. It is widely used in telecommunications, computers, and other digital systems for synchronizing signals, generating stable frequencies, and recovering a signal from noise.

### ii) Digital-to-Analog Converter
A Digital-to-Analog Converter (DAC) is a device that converts digital data, usually in the form of binary numbers, into an analog signal. This is commonly used in audio systems to convert digital audio files into analog signals that can be played through speakers or headphones.

Commands used to run the rvmyth.v file

```bash
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
```

After this we dump the ./pre_synth_sim.out file to create the .vcd file using the following command

```bash
./pre_synth_sim.out
```

We then run this .vcd file on gtkwave to observe the output

```bash
gtkwave pre_synth_sim.vcd
```
## Running the Command

![RunCommand](https://github.com/user-attachments/assets/d33dfeaf-d65c-4a96-8c9e-b701a666277e)

## Output Waveform 

![Output Waveform](https://github.com/user-attachments/assets/74381a4a-b744-463c-ba5d-d271e00f3881)

# Task10 : RTL design using Verilog with SKY130 Technology 

## Installation
```
sudo -i
sudo apt-get install git
ls
cd /home/bibinbjacob
mkdir VLSI
cd VLSI
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
ls
```
![Inst1](https://github.com/user-attachments/assets/8b94f035-f345-40a0-b62d-385082aba6e5)

The below consists of the verilog files used in this lab:

![Inst2](https://github.com/user-attachments/assets/bf6d25a8-e631-42af-84a0-0bd710f296fa)

## Day1 Introduction to Verilog RTL design and Synthesis

Run the following commands to simulate the verilog code 'good_mux.v'. The first line will compile and check for syntax errors in both the design and testbench. An executable file 'a.out' is generated on successful compilation. On executing a.out, a vcd file is generated that captures changes in the input and output values. GTKWave is used to view the waveforms

```
iverilog good_mux.v tb_good_mux.v
./a.out
gtkwave tb_good_mux.vcd
```
![GTK1](https://github.com/user-attachments/assets/68e8e62d-91b3-46e0-8475-bb12a9cdad0c)

**Code for good_mux.v :**

```
module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule

```

**Code for tb_good_mux.v :**

```
`timescale 1ns / 1ps
module tb_good_mux;
	// Inputs
	reg i0,i1,sel;
	// Outputs
	wire y;

        // Instantiate the Unit Under Test (UUT)
	good_mux uut (
		.sel(sel),
		.i0(i0),
		.i1(i1),
		.y(y)
	);

	initial begin
	$dumpfile("tb_good_mux.vcd");
	$dumpvars(0,tb_good_mux);
	// Initialize Inputs
	sel = 0;
	i0 = 0;
	i1 = 0;
	#300 $finish;
	end

always #75 sel = ~sel;
always #10 i0 = ~i0;
always #55 i1 = ~i1;
endmodule

```
Synthesizer is the tool used for converting the RTL to netlist. Yosys is one such open source synthesizer. Yosys optimizes the design, mapping it to specific target technology libraries or FPGA architectures, and generates an optimized netlist that can be further analyzed and prepared for physical layout and fabrication.

**Yosys Flow**

![image](https://github.com/user-attachments/assets/b70ab253-cba9-41eb-9d5b-ad23971384cd)

**Verify the Synthesis**

The same testbench that is used for the simulation can be used for the synthesized netlist as well.

![image](https://github.com/user-attachments/assets/6e56fdd0-c17e-4dad-b4c2-0b8c3828b904)

Synthesis has three steps: RTL to Gate level translation, The design is then converted into gates and the connections are made between the gates and the output is given out as a file called netlist

![image](https://github.com/user-attachments/assets/2922bb42-598d-4303-a9fc-697789ebace9)

**Liberty(.lib):** Its a collection of logical modules. It includes basic logic gates like And, Or, Not, etc... and it contains different variants of the same gate ike 2input, 3input, 4input, slow, fast, medium gates etc. Fast cells are used if only high performance is needed. Slower cells is used to address hold time issues. IThe selection of faster cells in digital circuit design can increase area and power consumption while potentially leading to hold time violations. Conversely, excessive use of slower cells can result in suboptimal performance. The optimal cell selection for synthesis is guided by constraints that balance area, power, and timing requirements.


The below is the Synthesis(Illustration)

![image](https://github.com/user-attachments/assets/6afc2127-2b77-4ab7-98ed-ee521977ec1c)

Use the below commands for synthesis:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog good_mux.v
synth -top good_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verlog good_mux_netlist.v
write_verilog -noattr good_mux_netlist.v
```
![Yosys](https://github.com/user-attachments/assets/0e97e047-4873-4f1b-b505-cab2e228b60c)

![V5](https://github.com/user-attachments/assets/0f01aa14-9e61-4d0f-9b74-173f6ae0a547)

![V6](https://github.com/user-attachments/assets/d49fa509-7a2a-4edb-ad77-4238a08b7119)

![V7](https://github.com/user-attachments/assets/49df58d6-2b2a-4946-9e48-d0d9304848ca)

## Day 2: Timing libs, hierarchical vs flat synthesis and efficient flop coding styles

Run the below commands to view the contents inside the .lib file:
```
cd ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/
vim sky130_fd_sc_hd__tt_025C_1v80.lib
```
![Screenshot from 2024-10-21 15-00-34](https://github.com/user-attachments/assets/b7f138bb-2edb-4fa1-8b7f-d74346c79a32)


The liberty(.lib) files store PVT parameters (Process, Voltage, Temperature). Variations in these parameters can significantly affect circuit performance. Manufacturing variations, voltage fluctuations, and temperature changes all contribute to this impact."

We can also find different versions of the same cell. For example, consider the AND gate
![Screenshot from 2024-10-21 15-33-54](https://github.com/user-attachments/assets/5736b89e-3611-45fd-bb68-f25eab84a1bc)
![Screenshot from 2024-10-21 15-33-46](https://github.com/user-attachments/assets/a4a6b15e-8754-4f2a-aaba-5bc36aaf89ec)
![Screenshot from 2024-10-21 15-33-36](https://github.com/user-attachments/assets/cd377b49-8d5f-49e7-9f89-b3048157bbb0)

We can observe that:

* and2_0 -- taking the least area, more delay and low power.
* and2_1 -- taking more area, less delay and high power.
* and2_2 -- taking the largest area, larger delay and highest power.


Hierarchical vs Flat Synthesis:

Hierarchical synthesis involves synthesizing a complex design by breaking it down into various sub-modules, where each module is synthesized separately to generate gate-level netlists and then integrated. Hierarchical synthesis allows for better organization, reuse of modules, and incremental changes to the design without affecting the entire system. Flat synthesis, on the other hand, treats the entire design as a single, monolithic unit during the synthesis process and regardless of any hierarchical relations, it is synthesized into a single netlist. Flat synthesis can be useful for optimizing certain designs but it becomes challenging to maintain, analyze, and modify the design due to its lack of structural modularity.

Consider the verilog file `multiple_modules.v` which is given in the verilog_files directory

```
module sub_module2 (input a, input b, output y);
    assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
    assign y = a&b;
endmodule


module multiple_modules (input a, input b, input c , output y);
    wire net1;
    sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
    sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule
```

To perform **hierarchical synthesis** on the `multiple_modules.v` file type the following commands:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show multiple_modules
write_verilog -noattr multiple_modules_hier.v
```

The following statistics are displayed:

![Screenshot from 2024-10-21 16-12-48](https://github.com/user-attachments/assets/3631463b-dd45-4e5b-962c-1c0e22b30e8f)

Netlist

![Screenshot from 2024-10-21 16-19-10](https://github.com/user-attachments/assets/35b29151-fd13-4f54-a630-892c4684a00d)

Hierarchical netlist code:

![Screenshot from 2024-10-21 16-26-22](https://github.com/user-attachments/assets/97d15ef2-2025-432d-8b09-070491fa00d1)

To perform **flat synthesis** on the `multiple_modules.v` file type the following commands:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
flatten
show
write_verilog -noattr multiple_modules_flat.v
```
The following statistics are displayed:

![Screenshot from 2024-10-21 18-20-53](https://github.com/user-attachments/assets/e20bb2a2-c735-45a7-8899-86e8c441ac80)

Netlist

![Screenshot from 2024-10-21 18-21-54](https://github.com/user-attachments/assets/367b89f1-99af-4084-9242-bc904888fa0c)

To perform **sub module synthesis**. type the below commands:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog multiple_modules.v 
synth -top sub_module
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
```


The following statistics are displayed:

![Screenshot from 2024-10-21 18-49-24](https://github.com/user-attachments/assets/3641ee73-89fd-476c-908b-2d95b20c180e)

Netlist

![Screenshot from 2024-10-21 18-49-45](https://github.com/user-attachments/assets/105f9371-806d-4909-86a9-17ca9bda6301)

*Flip-Flop Coding Styles and Optimizations**

Flip-Flops are an essential part of sequential logic in a circuit and here we explore the design and synthesis of various types of flip-flops. To prevent glitches in digital circuits, we use flip-flops to store intermediate values. This ensures that combinational circuit inputs remain stable until the clock edge, avoiding glitches and maintaining correct operation:

**Asynchronous Reset Flip-flop:**

Verilog Code:

```
module dff_asyncres ( input clk ,  input async_reset , input d , output reg q );
always @ (posedge clk , posedge async_reset)
begin
	if(async_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

Run the below code to view the simulation:

```
iverilog dff_asyncres.v tb_dff_asyncres.v
./a.out
gtkwave tb_dff_asyncres.vcd
```
Waveform
![Screenshot from 2024-10-21 19-09-04](https://github.com/user-attachments/assets/8cfe2f10-f8a3-4a7f-be02-4ddb127528dc)

Run the below code to view the netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_asyncres.v
synth -top dff_asyncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

Netlist:

![image](https://github.com/user-attachments/assets/70d7f947-f0e6-4921-b143-5f7419cf3ef6)

**Synchronous Reset Flip-flop:**

Verilog Code:

```
module dff_syncres ( input clk , input async_reset , input sync_reset , input d , output reg q );
always @ (posedge clk )
begin
	if (sync_reset)
		q <= 1'b0;
	else	
		q <= d;
end
endmodule
```

Run the below code to view the simulation:

```
iverilog dff_syncres.v tb_dff_syncres.v
./a.out
gtkwave tb_dff_syncres.vcd
```

Waveform:

![image](https://github.com/user-attachments/assets/8b80edd0-efdb-4ca7-9e4c-7db904655d20)

Run the below code to view the netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_syncres.v
synth -top dff_syncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

Netlist:

![image](https://github.com/user-attachments/assets/00399402-3299-4fa0-b672-0e97a2009683)

**Asynchronous Set Flip-flop:**

Verilog Code:

```
module dff_async_set ( input clk ,  input async_set , input d , output reg q );
always @ (posedge clk , posedge async_set)
begin
	if(async_set)
		q <= 1'b1;
	else	
		q <= d;
end
endmodule
```

Run the below code to view the simulation:

```
iverilog dff_async_set.v tb_dff_async_set.v
./a.out
gtkwave tb_dff_async_set.vcd
```

Waveform:

![image](https://github.com/user-attachments/assets/ec901aae-f8a9-4b23-8296-87dda912fc07)

Run the below code to view the netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_async_set.v
synth -top dff_async_set
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

Netlist:

![image](https://github.com/user-attachments/assets/a6b6a03b-0b96-467b-9ad8-3367e746b676)


**Optimizations:**

Example 1:

Consider the verilog code 'mult_2.v' :

```
module mul2 (input [2:0] a, output [3:0] y);
assign y = a * 2;
endmodule
```

Truth Table:

| a2 | a1 | a0 | y3 | y2 | y1 | y0 |
|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 | 1 | 0 |

We can see the multiplication of a number by 2 doesnt really need any extra hardware we just need to append the LSB's with zeroes and the remaining bits are the input bits of same, It can be realised by grouding the LSB's and wiring the input properly to the output.


Run the below code to view the netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_2.v
synth -top mul2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr mult_2_net.v
```
![Screenshot from 2024-10-21 19-49-23](https://github.com/user-attachments/assets/5e00f23e-97c4-4188-ada3-056a3a9b6e9f)

Netlist

![Screenshot from 2024-10-21 19-53-36](https://github.com/user-attachments/assets/392770d0-4f3a-42ba-b569-cb834c80ad5b)

Example 2:

Consider the verilog code 'mult_8.v' :

```
module mult8 (input [2:0] a , output [5:0] y);
	assign y = a * 9;
endmodule
```

In this design the 3-bit input number "a" is multiplied by 9 i.e (a*9) which can be re-written as (a*8) + a . The term (a*8) is nothing but a left shifting the number a by three bits. Consider that a = a2 a1 a0. (a*8) results in a2 a1 a0 0 0 0. (a*9)=(a*8)+a = a2 a1 a0 a2 a1 a0 = aa(in 6 bit format). Hence in this case no hardware realization is required. The synthesized netlist of this design is shown below:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_8.v
synth -top mult8
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr mult_8_net.v
```
![Screenshot from 2024-10-21 20-07-22](https://github.com/user-attachments/assets/4bafd265-529c-4394-8470-181feaf92424)



Netlist:

![Screenshot from 2024-10-21 20-09-55](https://github.com/user-attachments/assets/294dc01f-a363-4cbf-a002-520fd6c1a934)

Netlist code: 

![image](https://github.com/user-attachments/assets/6917d5ef-b1bf-4f0d-9ea1-8c794a2f1bf8)



### Day 3: Combinational and sequential optimizations

There are two types of optimisations: Combinational and Sequential optimisations. These optimisations are done inorder to achieve designs that are efficient in terms of area, power, and performance.

**Combinational Optimization**

The techiniques used are:

- Constant Propagation (Direct Optimisation)
- Boolean Logic Optimisation (using K-Map or Quine McCluskey method)

**Constant Propagation:**

Consider the below circuit:

![image](https://github.com/user-attachments/assets/24fcec7b-7b46-4d73-b93d-a257883ef6e5)

The top circuit uses 6 transistors(3 nmos and 3 pmos). The bottom cicuit uses 2 transistors(1 nmos and 1 pmos) when we make A zero as the logic becomes invertor. 

**Boolean Logic Optimisation:**

Consider the below verilog code:

`assign y = a?(b?c:(c?a:0)):(!c);`

The ternary operator (?:) will realize a mux 

**Example 1:**

Verllog code:

```
module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule
```

The above code infers a multiplexer and since one of the inputs of the multiplexer is always connected to the ground it will infer an AND gate on optimisation.

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v
synth -top opt_check
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr opt_check_net.v
```


![Screenshot from 2024-10-21 21-20-18](https://github.com/user-attachments/assets/420b16cc-51d4-4f1d-ad29-d04f6f7df92c)

Netlist

![Screenshot from 2024-10-21 21-22-55](https://github.com/user-attachments/assets/75117042-f0d9-4d2c-8987-9c92821de15e)

![Screenshot from 2024-10-21 21-25-36](https://github.com/user-attachments/assets/b4022cb3-71db-430d-a47c-c3ff2119c098)

**Example 2:**

Verllog code:

```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule
```

Since one of the inputs of the multiplexer is always connected to the logic 1 it will infer an OR gate on optimisation.The OR gate will be NAND implementation since NOR gate has stacked pmos while NAND implementation has stacked nmos.

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check2.v
synth -top opt_check2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr opt_check2_net.v
```

![Screenshot from 2024-10-21 21-32-58](https://github.com/user-attachments/assets/bb4b2e65-5fa0-467d-b497-69a89d39fa30)

Netlist

![Screenshot from 2024-10-21 21-34-24](https://github.com/user-attachments/assets/aaf256dc-dbb4-41f7-9509-f3ae8f6b8d1f)

**Example 3:**

Verilog code:

```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```

On optimisation the above design becomes a 3 input AND gate.

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check3.v
synth -top opt_check3
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr opt_check3_net.v
```

![Screenshot from 2024-10-21 21-54-21](https://github.com/user-attachments/assets/91b6e371-e88b-499e-8911-e5ea460b3c19)


Netlist

![Screenshot from 2024-10-21 21-54-59](https://github.com/user-attachments/assets/19615e92-822b-4525-899e-266669c8c492)

**Example 4:**

Verilog code:

```
module opt_check4 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```

On optimisation the above design becomes a 2 input XNOR gate.

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check4.v
synth -top opt_check4
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr opt_check4_net.v
```

![Screenshot from 2024-10-21 22-00-07](https://github.com/user-attachments/assets/cdff6503-e5ab-4365-895e-6f11f9773739)


Netlist

![Screenshot from 2024-10-21 22-02-30](https://github.com/user-attachments/assets/cec024da-38d5-407e-a155-eca6d27a43c6)

![Screenshot from 2024-10-21 22-07-58](https://github.com/user-attachments/assets/9c8a91a8-368e-41ca-a626-b5477357f859)


**Example 5:**

Verilog code:

```
module sub_module1(input a , input b , output y);
 assign y = a & b;
endmodule

module sub_module2(input a , input b , output y);
 assign y = a^b;
endmodule

module multiple_module_opt(input a , input b , input c , input d , output y);
wire n1,n2,n3;

sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
sub_module2 U3 (.a(b), .b(d) , .y(n3));

assign y = c | (b & n1); 

endmodule
```

On optimisation the above design becomes a AND OR gate

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_module_opt.v
synth -top multiple_module_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
flatten
show
write_verilog -noattr multiple_module_opt_net.v
```
![Screenshot from 2024-10-21 22-11-00](https://github.com/user-attachments/assets/9230cbf1-a099-40c4-bd86-7c708e691dfb)

Netlist
![Screenshot from 2024-10-21 22-16-11](https://github.com/user-attachments/assets/018eed9e-afc5-4802-9150-08ae3272b86d)


**Example 6:**

Verilog code:

```
module sub_module(input a , input b , output y);
	assign y = a & b;
endmodule

module multiple_module_opt2(input a , input b , input c , input d , output y);
		wire n1,n2,n3;
	sub_module U1 (.a(a) , .b(1'b0) , .y(n1));
	sub_module U2 (.a(b), .b(c) , .y(n2));
	sub_module U3 (.a(n2), .b(d) , .y(n3));
	sub_module U4 (.a(n3), .b(n1) , .y(y));
endmodule
```

On optimisation the above design becomes Y=0 

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_module_opt2.v
synth -top multiple_module_opt2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
flatten
show
write_verilog -noattr multiple_module_opt2_net.v
```
![Screenshot from 2024-10-21 22-22-01](https://github.com/user-attachments/assets/67840ad5-6591-419e-9e6d-4754aec98dda)

Netlist

![Screenshot from 2024-10-21 22-24-03](https://github.com/user-attachments/assets/b8f23eb5-8680-470d-b76e-399b898e4fba)

![image](https://github.com/user-attachments/assets/e7fd979b-c463-4e31-9ba0-52f98bb7a736)

**Sequential Logic Optimizations**

**Example 1:**

Verilog code:

```
module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule
```

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const1.v
synth -top dff_const1
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr dff_const1_net.v
```

![Screenshot from 2024-10-21 22-33-55](https://github.com/user-attachments/assets/3b9a8096-05ae-4789-8569-21cc808bd114)

Netlist

![Screenshot from 2024-10-21 22-34-55](https://github.com/user-attachments/assets/2b63c55c-b701-4958-85a4-6832563097bf)


![Screenshot from 2024-10-21 22-37-02](https://github.com/user-attachments/assets/95910db1-5017-42bb-9377-bdf194cb7b09)

GTKWave Output:

```
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```

![Screenshot from 2024-10-21 22-41-20](https://github.com/user-attachments/assets/01fc87bf-a411-44fc-b4f2-bf03c3e48497)

**Example 2:**

Verilog code:

```
module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule
```

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const2.v
synth -top dff_const2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr dff_const2_net.v
```

![Screenshot from 2024-10-21 22-47-07](https://github.com/user-attachments/assets/1ff9aa34-59ba-48d1-ba93-2d11851924dc)

netlist

![Screenshot from 2024-10-21 22-49-05](https://github.com/user-attachments/assets/7cd794f6-f087-45c0-80de-7153ab2d81e6)

![Screenshot from 2024-10-21 22-51-02](https://github.com/user-attachments/assets/3ef042fc-e5c1-4791-b8ad-ae2891a68bd9)

GTKWave Output:

```
iverilog dff_const2.v tb_dff_const2.v
./a.out
gtkwave tb_dff_const2.vcd
```
![Screenshot from 2024-10-21 22-54-18](https://github.com/user-attachments/assets/ba03a0c5-1d25-4634-84ad-b9f63d5da13e)

**Example 3:**

Verilog code:

```
module dff_const3(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b0;
	end
	else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end
endmodule
```

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const3.v
synth -top dff_const3
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr dff_const3_net.v
```
![Screenshot from 2024-10-21 23-09-56](https://github.com/user-attachments/assets/f440f379-bde4-4b6f-a2fc-c0757be367df)

netlist

![Screenshot from 2024-10-21 23-12-41](https://github.com/user-attachments/assets/01ded03f-f025-4d10-a0c5-098e185ec7c6)


![Screenshot from 2024-10-21 23-15-01](https://github.com/user-attachments/assets/88b6db8c-112f-4e52-9de6-87e127027af0)

GTKWave Output:

```
iverilog dff_const3.v tb_dff_const3.v
./a.out
gtkwave tb_dff_const3.vcd
```
![Screenshot from 2024-10-21 23-21-04](https://github.com/user-attachments/assets/e4a9650c-922d-43da-a2ff-7b8a22a16330)

**Example 4:**

Verilog code:

```
module dff_const4(input clk, input reset, output reg q);
reg q1;

always @(posedge clk, posedge reset)
begin
	if(reset)
	begin
		q <= 1'b1;
		q1 <= 1'b1;
	end
else
	begin
		q1 <= 1'b1;
		q <= q1;
	end
end
endmodule
```

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const4.v
synth -top dff_const4
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr dff_const4_net.v
```

![Screenshot from 2024-10-21 23-31-42](https://github.com/user-attachments/assets/5a3cd3e9-1aee-415f-8d72-898814f3483d)

Netlist

![Screenshot from 2024-10-21 23-31-50](https://github.com/user-attachments/assets/201d674e-bdae-4adf-8336-777cb128b28d)

![Screenshot from 2024-10-21 23-35-05](https://github.com/user-attachments/assets/54d0dcae-28ef-4799-96ac-6b28b3ded051)

GTKWave Output:

```
iverilog dff_const4.v tb_dff_const4.v
./a.out
gtkwave tb_dff_const4.vcd
```
![Screenshot from 2024-10-21 23-38-17](https://github.com/user-attachments/assets/53ec38cb-0d2d-4ab3-a90e-a5454f65e91a)

**Example 5:**

Verilog code:

```
module dff_const5(input clk, input reset, output reg q);
reg q1;
always @(posedge clk, posedge reset)
	begin
		if(reset)
		begin
			q <= 1'b0;
			q1 <= 1'b0;
		end
	else
		begin
			q1 <= 1'b1;
			q <= q1;
		end
	end
endmodule
```

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const5.v
synth -top dff_const5
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr dff_const5_net.v
```
![Screenshot from 2024-10-21 23-42-01](https://github.com/user-attachments/assets/54e0abab-7469-4eab-9def-c87478c2679e)

netlist
![Screenshot from 2024-10-21 23-43-18](https://github.com/user-attachments/assets/96c30ad0-0f72-4359-94ab-c72bdba276e7)

![Screenshot from 2024-10-21 23-45-25](https://github.com/user-attachments/assets/69f68217-d221-4c3b-bef3-23373da968a7)

GTKWave Output:

```
iverilog dff_const5.v tb_dff_const5.v
./a.out
gtkwave tb_dff_const5.vcd
```

![Screenshot from 2024-10-21 23-47-26](https://github.com/user-attachments/assets/3429d262-933e-416c-b5d2-d361ebef2eab)

**Sequential Logic Optimizations for unused outputs**

**Example 1:**

Verilog code:

```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];
always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end
endmodule
```

Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr counter_opt_net.v
```
![Screenshot from 2024-10-21 23-47-26](https://github.com/user-attachments/assets/08de08d2-aa70-4d9b-84e2-398635af898d)

Netlist
![Screenshot from 2024-10-21 23-51-24](https://github.com/user-attachments/assets/79ea28e7-adac-4bf1-9970-4e6f75c3314c)

![Screenshot from 2024-10-21 23-53-49](https://github.com/user-attachments/assets/c5b1cf7e-200a-4897-8706-aff2c0f6bfb2)


GTKWave Output:

```
iverilog counter_opt.v tb_counter_opt.v
./a.out
gtkwave tb_counter_opt.vcd
```
![Screenshot from 2024-10-21 23-57-08](https://github.com/user-attachments/assets/fb6c6cdd-d9e2-41c3-a37c-c0d59bb2d75e)

Modified counter logic:

Verilog code:

```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = {count[2:0]==3'b100};
always @(posedge clk ,posedge reset)
begin
if(reset)
	count <= 3'b000;
else
	count <= count + 1;
end
endmodule
```
Run the below code for netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr counter_opt_net.v
```
![Screenshot from 2024-10-21 23-59-14](https://github.com/user-attachments/assets/e0ca8f6b-cea1-4502-a2e9-835cca7e0c51)

netlist
![Screenshot from 2024-10-22 00-00-58](https://github.com/user-attachments/assets/09b02bbd-dd98-44fa-857e-47874a0aa8ac)

![Screenshot from 2024-10-22 00-02-31](https://github.com/user-attachments/assets/b54c1f9a-2655-46ff-aa57-fd3bd6a8303a)

GTKWave Output:

```
iverilog counter_opt.v tb_counter_opt.v
./a.out
gtkwave tb_counter_opt.vcd
```
![Screenshot from 2024-10-22 00-05-11](https://github.com/user-attachments/assets/30ad2aef-1e2e-476f-befa-c75b5b35ec02)

### Day 4: GLS, blocking vs non-blocking and Synthesis-Simulation mismatch

Gate Level Simulation (GLS) is a crucial step in the verification process of digital circuits. It involves simulating the synthesized netlist, which is a lower-level representation of the design, using a testbench to verify its logical correctness and timing behavior. By comparing the simulated outputs to the expected outputs, GLS ensures that the synthesis process has not introduced any errors and that the design meets its performance requirements.

![image](https://github.com/user-attachments/assets/fa59f230-4a0d-4c8e-9353-a01a9209a6d6)

Sensitivity lists are crucial for accurate circuit behavior. If a sensitivity list is incomplete, it can lead to unexpected latches. Blocking and non-blocking assignments within always blocks have different execution behaviors. Incorrect use of blocking assignments can unintentionally create latches, causing synthesis and simulation mismatches. To avoid these issues, it's essential to carefully analyze circuit behavior and ensure that the sensitivity list and assignments align with the desired functionality.

**GLS Simulation**

**Example 1:**

Verilog code:

```
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
assign y = sel?i1:i0;
endmodule
```

Simulation:

```
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```
![Screenshot from 2024-10-22 00-13-01](https://github.com/user-attachments/assets/2c536a59-4522-49f9-93f4-e886828a81ef)

Netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr ternary_operator_mux_net.v
```

![Screenshot from 2024-10-22 00-16-52](https://github.com/user-attachments/assets/035681ac-6509-44b2-a39e-f2f653b09411)

Netlist

![Screenshot from 2024-10-22 00-17-39](https://github.com/user-attachments/assets/adf9bcba-9028-4763-b168-9b48b81e397e)

![Screenshot from 2024-10-22 00-18-40](https://github.com/user-attachments/assets/04652c3b-d527-4437-aaa9-8fd1eecf5230)

GLS:

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

![Screenshot from 2024-10-22 00-21-00](https://github.com/user-attachments/assets/2473a877-810f-4819-8485-afb26863f1f8)

In this case there is no mismatch between the waveforms before and after synthesis

**Example 2:**

Verilog code:

```
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
end
endmodule
```

Simulation:

```
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
![Screenshot from 2024-10-22 00-22-45](https://github.com/user-attachments/assets/dc6a625f-96df-4c65-bcb7-d1e5cea4093c)

Netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog bad_mux.v
synth -top bad_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr bad_mux_net.v
```
![Screenshot from 2024-10-22 00-27-08](https://github.com/user-attachments/assets/b75dc4b2-483c-43f1-8fdd-6a93b0f2de6f)

netlist
![Screenshot from 2024-10-22 00-28-39](https://github.com/user-attachments/assets/9f74b69b-b2f3-4803-a9ff-a19eb220f879)

![image](https://github.com/user-attachments/assets/93f06a14-81f9-4eb8-b2c5-4d87cf7a0ea6)

GLS:

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
![Screenshot from 2024-10-22 00-31-22](https://github.com/user-attachments/assets/d32cb807-b23d-42cb-8a39-912148e8bb16)

In this case there is a synthesis and simulation mismatch. While performing synthesis yosys has corrected the sensitivity list error.

**Labs on Synthesis-Simulation mismatch for blocking statements**

Verilog code:

```
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
d = x & c;
x = a | b;
end
endmodule
```

Simulation:

```
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
![Screenshot from 2024-10-22 00-34-49](https://github.com/user-attachments/assets/587bbf84-d9e1-4e04-80f5-afdc1eeee36b)

Netlist:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show
write_verilog -noattr blocking_caveat_net.v
```
![Screenshot from 2024-10-22 00-37-48](https://github.com/user-attachments/assets/19ee1879-1548-4eb3-82f8-1b5306f2a1e0)
netlist
![Screenshot from 2024-10-22 00-39-01](https://github.com/user-attachments/assets/6231ace6-aeb2-4809-8c45-e011173329d2)

![Screenshot from 2024-10-22 00-40-21](https://github.com/user-attachments/assets/0ea333fb-c285-44bf-82d2-7158125299f8)

GLS:

```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
![Screenshot from 2024-10-22 00-41-29](https://github.com/user-attachments/assets/9dd8723d-b860-4265-b2ab-af58d0d496e5)

In this case there is a synthesis and simulation mismatch. While performing synthesis yosys has corrected the latch error.

### Task 11 : RISC-V Synthesis for Gate-Level Simulation of BabySoC:

## O1 result of Presynthesis

### Terminal
![Screenshot from 2024-10-24 18-10-24](https://github.com/user-attachments/assets/79d54ae0-533b-40ff-9c6f-0a68cc614e9b)


### Waveform

![Screenshot from 2024-10-24 17-41-25](https://github.com/user-attachments/assets/5159ff68-55b2-4282-a4bc-33164d1c6c20)

## O2 result of Postsynthesis

### Terminal

![Screenshot from 2024-10-24 18-13-37](https://github.com/user-attachments/assets/8a005f70-b61b-4674-bda5-09bb090d17b2)

### Waveform

![Screenshot from 2024-10-24 18-34-55](https://github.com/user-attachments/assets/6abf9567-6b81-48e0-b534-e86d6e8478a2)


### O1= O2 The pre synthesis simulation waveforms and the post synthesis simulation waveforms were found to be identical.

# Lab 11 -  Static Timing Analysis for a Synthesized RISC-V Core with OpenSTA 

### Static time analysis  
Static Timing Analysis (STA) verifies the timing performance of a digital circuit without dynamic simulation, checking if it meets timing constraints by analyzing timing paths. STA evaluates paths from input to output, considering delays of gates and interconnects. It checks for setup and hold time violations, ensuring data stability before and after clock edges. STA also incorporates clock definitions, including frequency and variations like skew or jitter, and assumes worst-case conditions for delays to ensure circuit performance under all conditions. Tools like Synopsys PrimeTime and Cadence Tempus automate this process, identifying timing issues early to ensure reliable circuit operation at intended speeds. STA is crucial for several reasons in digital circuit design. It verifies that data signals can propagate within required time limits, ensuring stable and valid outputs. It helps identify timing violations, ensuring reliable operation of flip-flops and sequential elements. STA allows designers to optimize performance by identifying and improving critical paths that limit the circuit's maximum operating frequency. It enables early detection of timing issues, reducing costly revisions later. STA also helps balance performance and power efficiency by analyzing the impact of clock frequency on power consumption. Automated STA tools efficiently analyze complex designs, incorporating variations in manufacturing, temperature, and voltage to ensure robust performance.  

### Reg2Reg Path   
A reg2reg path connects two sequential elements, like flip-flops, in a digital circuit. This path is essential in STA for verifying data flow from one register to another through combinational logic. Reg2reg paths ensure proper data flow and synchronization, especially in designs with pipelining or sequential operations. They are analyzed for setup and hold time constraints, ensuring data stability at the registers. Timing analysis includes delays through combinational logic connecting the registers. Critical reg2reg paths limit the circuit's maximum operating frequency, requiring optimization. If registers belong to different clock domains, additional considerations for metastability and synchronization are needed.  

### Clk2Reg Path    
A clk2reg path connects the clock signal to a register in a digital circuit, ensuring the register operates correctly in response to clock events. This path represents the time it takes for the clock signal to reach the register from the clock source, including delays from clock buffers or routing. In setup timing analysis, it determines when data must arrive at the register relative to the clock edge. Clock delay through distribution elements impacts the timing of data capture at the register. While primarily for setup time analysis, clk2reg paths also consider hold time, especially with clock jitter or variations. Analysis includes considerations for synchronization in different clock domains.   

### STA for synthesized Risc-V core using time period of 10.05 seconds  
In this task, we'll generate setup and hold timing reports for our synthesized RISC-V Core module. These reports are essential for verifying that the circuit meets its timing constraints, ensuring data signals propagate correctly through the core  


## Tools Installation
**CUDD**

```
cd
tar xvfz cudd-3.0.0.tar.gz
cd cudd-3.0.0
./configure
make
```
**openSTA**
```
cd
sudo apt-get install cmake clang gcc tcl swig bison flex

git clone https://github.com/parallaxsw/OpenSTA.git
cd OpenSTA
cmake -DCUDD_DIR=/home/bibin-b-jacob/cudd-3.0.0
make
app/sta
```

![Screenshot from 2024-10-29 00-31-59](https://github.com/user-attachments/assets/5d3e939b-bff4-498f-a723-6c494ec52556)

**Steps to do Timing Analysis**
- Clock period = 10.05ns
- Setup uncertainty and clock transition will be 5% of clock
- Hold uncertainty and data transition will be 8% of clock. 

```
cd /home/bibin-b-jacob/OpenSTA/app
./sta

read_liberty /home/bibin-b-jacob/OpenSTA/Directory/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog /home/bibin-b-jacob/OpenSTA/Directory/bibin_riscv_netlist.v
link_design rvmyth

create_clock -name clk -period 10.05 [get_ports clk]
set_clock_uncertainty [expr 0.05 * 10.05] -setup [get_clocks clk]
set_clock_uncertainty [expr 0.08 * 10.05] -hold [get_clocks clk]
set_clock_transition [expr 0.05 * 10.05] [get_clocks clk]
set_input_transition [expr 0.08 * 10.05] [all_inputs]

report_checks -path_delay max
report_checks -path_delay min

```
![Screenshot from 2024-10-29 00-37-51](https://github.com/user-attachments/assets/549d259b-dfda-42c7-b962-44651d52e46f)


![Screenshot from 2024-10-29 00-39-02](https://github.com/user-attachments/assets/5cae14aa-c576-4810-8f71-4092c8ccfd72)

# Lab 12 - Perform Static Timing Analysis on the synthesized RISC-V netlistusing different PVT files. 

### vsdbabysoc_synthesis.sdc
- Clock period = 10.05ns
- Setup uncertainty and clock transition is 5% of clock
- Hold uncertainty and data transition is 8% of clock. 
```
# Create clock with new period
create_clock [get_pins pll/CLK] -name clk -period 10.05 -waveform {0 4.725}

# Set loads
set_load -pin_load 0.5 [get_ports OUT]
set_load -min -pin_load 0.5 [get_ports OUT]

# Set clock latency
set_clock_latency 1 [get_clocks clk]
set_clock_latency -source 2 [get_clocks clk]

# Set clock uncertainty
set_clock_uncertainty 0.5025 [get_clocks clk]  ; # 5% of clock period for setup
set_clock_uncertainty -hold 0.804 [get_clocks clk] ; # 8% of clock period for hold

# Set maximum delay
set_max_delay 10.05 -from [get_pins dac/OUT] -to [get_ports OUT]

# Set input delay for VCO_IN
set_input_delay -clock clk -max 4 [get_ports VCO_IN]
set_input_delay -clock clk -min 1 [get_ports VCO_IN]

# Set input delay for ENb_VCO
set_input_delay -clock clk -max 4 [get_ports ENb_VCO]
set_input_delay -clock clk -min 1 [get_ports ENb_VCO]

# Set input delay for ENb_CP
set_input_delay -clock clk -max 4 [get_ports ENb_CP]
set_input_delay -clock clk -min 1 [get_ports ENb_CP]

# Set input transition for VCO_IN
set_input_transition -max 0.5025 [get_ports VCO_IN] ; # 5% of clock
set_input_transition -min 0.804 [get_ports VCO_IN] ; # adjust if needed

# Set input transition for ENb_VCO
set_input_transition -max 0.5025 [get_ports ENb_VCO] ; # 5% of clock
set_input_transition -min 0.804 [get_ports ENb_VCO] ; # adjust if needed

# Set input transition for ENb_CP
set_input_transition -max 0.5025 [get_ports ENb_CP] ; # 5% of clock
set_input_transition -min 0.804 [get_ports ENb_CP] ; # adjust if needed
```


### sta.tcl

```
   set list_of_lib_files(1) "sky130_fd_sc_hd__tt_025C_1v80.lib"
set list_of_lib_files(2) "sky130_fd_sc_hd__tt_100C_1v80.lib"
set list_of_lib_files(3) "sky130_fd_sc_hd__ff_100C_1v65.lib"
set list_of_lib_files(4) "sky130_fd_sc_hd__ff_100C_1v95.lib"
set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
set list_of_lib_files(7) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
set list_of_lib_files(8) "sky130_fd_sc_hd__ff_n40C_1v95.lib"
set list_of_lib_files(9) "sky130_fd_sc_hd__ss_100C_1v40.lib"
set list_of_lib_files(10) "sky130_fd_sc_hd__ss_100C_1v60.lib"
set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
set list_of_lib_files(14) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
set list_of_lib_files(15) "sky130_fd_sc_hd__ss_n40C_1v60.lib"
set list_of_lib_files(16) "sky130_fd_sc_hd__ss_n40C_1v76.lib"

for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
read_liberty /home/bibin-b-jacob/OpenSTA/lab/lib/$list_of_lib_files($i)
read_liberty -min /home/bibin-b-jacob/OpenSTA/lab/lib/avsdpll.lib
read_liberty -max /home/bibin-b-jacob/OpenSTA/lab/lib/avsdpll.lib
read_liberty -min /home/bibin-b-jacob/OpenSTA/lab/lib/avsddac.lib
read_liberty -max /home/bibin-b-jacob/OpenSTA/lab/lib/avsddac.lib
read_verilog  /home/bibin-b-jacob/OpenSTA/lab/vsdbabysoc_synth.v
link_design vsdbabysoc
read_sdc /home/bibin-b-jacob/OpenSTA/lab/vsdbabysoc_synthesis.sdc
check_setup -verbose
report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > /home/bibin-b-jacob/OpenSTA/lab/output/min_max_$list_of_lib_files($i).txt

exec echo "$list_of_lib_files($i)" >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_worst_max_slack.txt
report_worst_slack -max -digits {4} >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_worst_max_slack.txt

exec echo "$list_of_lib_files($i)" >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_worst_min_slack.txt
report_worst_slack -min -digits {4} >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_worst_min_slack.txt

exec echo "$list_of_lib_files($i)" >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_tns.txt
report_tns -digits {4} >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_tns.txt

exec echo "$list_of_lib_files($i)" >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_wns.txt
report_wns -digits {4} >> /home/bibin-b-jacob/OpenSTA/lab/output/sta_wns.txt
}

```

### Commands to perform STA

```
cd OpenSTA/app
./sta
source /home/bibin-b-jacob/OpenSTA/lab/sta.tcl
```
![Screenshot from 2024-11-05 19-03-30](https://github.com/user-attachments/assets/1048beea-9edc-4221-b340-4f62504e7abe)

| Library File                          |         TNS         |         WNS         |     Worst Max Slack (or) Worst Setup Slack    |     Worst Min Slack (or) Worst Hold Slack     |
|---------------------------------------|:-------------------:|:-------------------:|:----------------------:|:-------------------------:|
| sky130_fd_sc_hd__tt_025C_1v80.lib    |       -2.3908       |       -0.0833       |         -0.0833        |          -0.4464         |
| sky130_fd_sc_hd__tt_100C_1v80.lib    |        0.0000       |        0.0000       |          0.0710        |          -0.4415         |
| sky130_fd_sc_hd__ff_100C_1v65.lib    |        0.0000       |        0.0000       |          2.0320        |          -0.5069         |
| sky130_fd_sc_hd__ff_100C_1v95.lib    |        0.0000       |        0.0000       |          3.5443        |          -0.5600         |
| sky130_fd_sc_hd__ff_n40C_1v56.lib    |        0.0000       |        0.0000       |          0.2556        |          -0.4645         |
| sky130_fd_sc_hd__ff_n40C_1v65.lib    |        0.0000       |        0.0000       |          1.3887        |          -0.5009         |
| sky130_fd_sc_hd__ff_n40C_1v76.lib    |        0.0000       |        0.0000       |          2.4076        |          -0.5317         |
| sky130_fd_sc_hd__ff_n40C_1v95.lib    |        0.0000       |        0.0000       |          3.5694        |          -0.5685         |
| sky130_fd_sc_hd__ss_100C_1v40.lib    |     -3305.4478      |      -19.1441       |        -19.1441        |           0.1493         |
| sky130_fd_sc_hd__ss_100C_1v60.lib    |     -1352.3196      |       -9.8965       |         -9.8965        |          -0.1140         |
| sky130_fd_sc_hd__ss_n40C_1v28.lib    |    -15136.6904      |      -64.5857       |        -64.5857        |           1.0736         |
| sky130_fd_sc_hd__ss_n40C_1v35.lib    |     -9084.4893      |      -41.7195       |        -41.7195        |           0.5915         |
| sky130_fd_sc_hd__ss_n40C_1v40.lib    |     -6459.7271      |      -31.7162       |        -31.7162        |           0.3689         |
| sky130_fd_sc_hd__ss_n40C_1v44.lib    |     -5001.8486      |      -25.9304       |        -25.9304        |           0.2349         |
| sky130_fd_sc_hd__ss_n40C_1v60.lib    |     -1876.7622      |      -12.6315       |        -12.6315        |          -0.0932         |
| sky130_fd_sc_hd__ss_n40C_1v76.lib    |      -735.8080      |       -6.4044       |         -6.4044        |          -0.2522         |

![Figure_1](https://github.com/user-attachments/assets/24914d62-569e-4d14-a320-41c5067143d1)
![Figure_2](https://github.com/user-attachments/assets/531d5e57-490a-4e76-ae34-e7c2afa9be60)


# Lab 13 - Advanced Physical Design Using Openlane

### Theory

<details>
  <summary>
Expand or Collapse
  </summary>

#### Package

* In any embedded board we have seen, the part of the board we consider as the chip is only the ***PACKAGE*** of the chip which is nothing but a protective layer or packet bound over the actual chip and the actual manufatured chip is usually present at the center of a package wherein, the connections from package is fed to the chip by ***WIRE BOUND*** method which is none other than basic wired connection.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7562205a-7435-46c7-a66e-de1626911f14)
![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7005a9e3-79da-4590-bea0-eb3768127a3d)
![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/70b1c678-2a2e-484f-9181-812dbcd5f0a3)

#### Chip

* Now, taking a look inside the chip, all the signals from the external world to the chip and vice versa is passed through ***PADS***. The area bound by the pads is ***CORE*** where all the digital logic of the chip is placed. Both the core and pads make up the ***DIE*** which is the basic manufacturing unit in regards to semiconductor chips.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d65a0ddf-2f86-4bbc-8d36-b02e09a1483e)

* ***FOUNDRY*** is the place where the semiconductor chips are manufactured and ***FOUNDRY IP's*** are Intellectual Properties based on a specific foundry and these IP's require a specific level of intelligence to be produced whereas, repeatable digital logic blocks are called ***MACROS***.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ed1cd25e-6270-4b84-8f0d-f0ea7c8a7ef8)

#### ISA (Intruction Set Architecture)

* A C program which has to be run on a specific hardware layout which is the interior of a chip in your laptop, there is certain flow to be followed.
* Initially, this particular C program is compiled in it's assembly language program which is nothing but ***RISC-V ISA (Reduced Instruction Set Compting - V Intruction Set Architecture)***.
* Following this, the assembly language program is then converted to machine language program which is the binary language logic 0 and 1 which is understood by the hardware of the computer.
* Directly after this, we've to implement this RISC-V specification using some ***RTL (a Hardware Description Language)***. Finally, from the RTL to ***Layout*** it is a standard PnR or RTL to GDSII flow.

![Screenshot (278)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7dc4601a-e386-48e5-9d1f-7fa5b47ca0ba)

* For an application software to be run on a hardware there are several processes taking place. To begin with, the apps enters into a block called system software and it converts the application program to binary language. There are various layers in system software in which the major layers or components are OS (Operating System), Compiler and Assembler.
* At first the OS outputs are small function in C, C++, VB or Java language which are taken by the respective compiler and converted into instructions and the syntax of these instructions varies with the hardware architecture on which the system is implemented.
* Then, the job of the assembler is to take these instructions and convert it into it's binary format which is basically called as a machine language program. Finally, this binary language is fed to the hardware and it understands the specific functions it has to perform based on the binary code it receives.

![Screenshot (279)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/19e8b634-f209-41a6-928d-6fba66f5b177)

* For example, if we take a stopwatch app on RISC-V core, then the output of the OS could be a small C function which enters into the compiler and we get output RISC-V instructions following this, the output of the assembler will be the binary code which enters into your chip layout.

![Screenshot (280)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/7d4570ca-82a6-4abe-81d2-067ebb9b2c15)

* For the above stopwatch the following are the input and output of the compiler and assembler.

![Screenshot (281)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/d7b7fd1b-21ee-46b7-9a91-8314bd753a51)

* The output of the compiler are instructions and the output of the assembler is the binary pattern. Now, we need some RTL (a Hardware Description Language) which understands and implements the particular instructions. Then, this RTL is synthesised into a netlist in form of gates which is fabricated into the chip through a physical design implementation.

![Screenshot (282)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/e349cb06-45e3-4ae4-b85f-9020a0a62737)

* There are mainly 3 different parts in this course. They are:
1. RISC-V ISA
2. RTL and synthesis of RISC-V based CPU core - picorv32
3. Physical design implementation of picorv32

![Screenshot (283)](https://github.com/fayizferosh/risc-v-myth-report/assets/63997454/832f0ea6-2d60-4d9a-937c-a2dedd5f8cac)

#### Open-source Implementation

* For open-source ASIC design implemantation, we require the following enablers to be readily available as open-source versions. They are:-
1. RTL Designs
2. EDA Tools
3. PDK Data

* Initially in the early ages, the design and fabrication of IC's were tightly coupled and were only practiced by very few companies like TI, Intel, etc.
* In 1979, Lynn Conway and Carver Mead came up with an idea to saperate the design from the fabrication and to do this they inroduced structured design methodologies based on the λ-based design rules and published the first VLSI book "Introduction to VLSI System" which started the VLSI education.
* This methodology resulted in the emergence of the design only companies or ***"Fabless Companies"*** and fabrication only companies that we usually refer to as ***"Pure Play Fabs"***.
* The inteface between the designers and the fab by now became a set of data files and documents, that are reffered to as the ***"Process Design Kits (PDKs)"***.
* The PDK include but not limited to Device Models, Technology Information, Design Rules, Digital Standard Cell Libraries, I/O Libraries and many more.
* Since, the PDK contained variety of informations, and so they were distributed only under NDAs (Non-Disclosure Agreements) which made it in-accessible to the public.
* Recently, Google worked out an agreement with skywater to open-source the PDK for the 130nm process by skywater Technology, as a result on 30 June 2020 Google released the first ever open-source PDK.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/87384374-e66b-4ec6-b9c4-3fb92ad4d275)

* ASIC design is a complex step that involves tons of steps, various methodologies and respective EDA tools which are all required for successful ASIC implementation which is achieved though an ASIC flow which is nothing but a piece of software that pulls different tools togather to carry out the design process.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/1762d6d6-c5f8-4bd9-8a3d-968eb4360889)

#### OpenLANE Open-source ASIC Design Implementation Flow

* The main objective of the ASIC Design Flow is to take the design from the RTL (Register Transfer Level) all the way to the GDSII, which is the format used for the final fabrication layout.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/533f58ee-4524-4a18-abb5-36b4d6a56b1f)

* Synthesis is the process of convertion or translation of design RTL into circuits made out of Standard Cell Libraries (SCL) the resultant circuit is described in HDL and is usually reffered to as the Gate-Level Netlist.
* Gate-Level Netlist is functionally equivalent to the RTL.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e43891a0-ab09-4df2-898d-7e843158e936)

* The fundemental building blocks which are the standard cells have regular layouts.
* Each cell has different views/models which are utilised by different EDA tools like liberty view with electrical models of the cells, HDL behavioral models, SPICE or CDL views of the cells, Layout view which include GDSII view which is the detailed view and LEF view which is the abstract view.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/48df884c-c894-4a2a-a511-09321c208d6b)

* Chip Floor Planning

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/38ecd866-ac83-42c7-83ba-2ba995f9ba4e)

* Macro Floor Planning

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/35ac760c-bba9-4bd1-9c65-e8ceeee2ccf5)

* Power Planning typically uses upper metal layers for power distribution since thay are thicker than lower metal layers and so have lower resistance and PP is done to avoid electron migration and IR drops.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/f18013a7-e4c7-4a6d-ba53-33362c04689a)

* Placement

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3654398b-40bc-4e42-9205-77f673d5584c)

* Global placement provide approximate locations for all cells based on connectivity but in this stage the cells may be overlapped on each other and in detailed placement the positions obtained from global placements are minimally altered to make it legal (non-overlapping and in site-rows)

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/817c504d-0b8e-4a0a-9c3c-e9d110c23535)

* Clock Tree Synthesis

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6db284d4-065f-450a-9200-a6e6cbfd7fbb)

* Clock skew is the time difference in arrival of clock at different components.
* Routing

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7458495f-b527-4f21-813e-8dbcbf29ed9b)

* skywater PDK has 6 routing layers in which the lowest layer is called the local interconnect layer which is a Titanium Nitride layer the following 5 layers are all Aluminium layers.

![stackup](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e4438c12-d83e-4083-a58f-33a410a47927)

* Global and Detailed Routing

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/b54ebd4c-127a-441f-829e-6000531e9b8d)

* Once done with the routing the final layout can be generated which undergoes various Sign-Off checks.
* Design Rules Checking (DRC) which verifies that the final layout honours all design fabrication rules.
* Layout Vs Schematic (LVS) which verifies that the final layout functionality matches the gate-level netlist that we started with.
* Static Timing Analysis (STA) to verify that the design runs at the designated clock frequency.

![image](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d8bc72cd-2fe9-4ae2-9431-68a6fa77c671)

</details>

## Day 1

1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
2. Calculate the flop ratio.

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ DFF's = Flop\ Ratio * 100
```
#### 1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.

Commands to invoke the OpenLANE flow and perform synthesis

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```

Screenshots of running each commands

![1](https://github.com/user-attachments/assets/7b2c3332-1307-42f4-98f4-b2e6a26f7069)

![2](https://github.com/user-attachments/assets/47f487c0-3bdb-4f4d-ba2b-52d6ce938345)

![3](https://github.com/user-attachments/assets/34ad6ed5-8987-4ee1-a238-2c79ec132bd9)

Calculating flop ratio

![4](https://github.com/user-attachments/assets/6f4f0056-8eb0-4403-bc64-ab7e5069b4da)

Calculation of Flop Ratio and DFF % from synthesis statistics report file

```math
Flop\ Ratio = \frac{1634}{19119} = 0.0854
```
```math
Percentage\ of\ DFF's = 0.0854 * 100 = 8.54\ \%
```
## Day 2


1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
2. Calculate the die area in microns from the values in floorplan def.
3. Load generated floorplan def in magic tool and explore the floorplan.
4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
5. Load generated placement def in magic tool and explore the placement.

```math
Area\ of\ die\ in\ microns = Die\ width\ in\ microns * Die\ height\ in\ microns
```

#### 1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.

Commands to invoke the OpenLANE flow and perform floorplan

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```

Screenshot of floorplan run

![1](https://github.com/user-attachments/assets/6b49ff2e-9e2e-4dbb-b053-530a2de88f7c)

![2](https://github.com/user-attachments/assets/bba93340-29bd-43e8-8c71-8b4f7741a1cb)

Calculate the die area in microns from the values in floorplan def.

![3](https://github.com/user-attachments/assets/5268d547-293d-499c-862d-dd74ed0efbc9)

According to floorplan def
```math
1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Square\ Microns
```
Load generated floorplan def in magic tool and explore the floorplan.

![4](https://github.com/user-attachments/assets/5102aff5-6cfc-407d-8d86-666675e45f9c)

![5](https://github.com/user-attachments/assets/5c5e482c-dfe6-4af9-b9d7-3828f33620f6)

Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.

Command to run placement

```tcl
# Congestion aware placement by default
run_placement
```
![6](https://github.com/user-attachments/assets/0f25c047-b8fe-4ce9-81f9-c93fedd3f2af)

Load generated placement def in magic tool and explore the placement.

![7](https://github.com/user-attachments/assets/4c3e3b4f-8047-4e44-90c9-34cb8f63a200)

Standard cells legally placed

![8](https://github.com/user-attachments/assets/73a2e5d9-a20a-4c6f-8f2f-0ba2db92c2b1)

# Day 3

Clone custom inverter standard cell design from github repository

![1](https://github.com/user-attachments/assets/0ce37f66-d172-40d0-9092-29d4a29647de)

 Load the custom inverter layout in magic and explore.

![2](https://github.com/user-attachments/assets/5f8cb896-f646-4470-9c6c-84cb5ed1d369)

Output Y connectivity to PMOS and NMOS drain verified

![3](https://github.com/user-attachments/assets/c125f3de-84a1-4f7c-b70e-b4a2fbb63f51)

NMOS source connectivity to VSS (here VGND) verified

![4](https://github.com/user-attachments/assets/202f8cd8-29b8-41f7-ae7d-ae1604f96697)

Deleting necessary layout part to see DRC error

![5](https://github.com/user-attachments/assets/94371c18-1572-474b-990d-8b65f6084ff8)

Spice extraction of inverter in magic.

![8](https://github.com/user-attachments/assets/b087c448-49ab-40f0-ad05-fc2508641f90)

Final edited spice file ready for ngspice simulation

![10](https://github.com/user-attachments/assets/f08fc8d1-ec66-41a2-a871-397ba41a1895)

Post-layout ngspice simulations.

![11](https://github.com/user-attachments/assets/d96523d9-6944-40a2-ad82-f61d2a0cf9d6)

![12](https://github.com/user-attachments/assets/d451f6d7-0810-44a6-a2c9-05d932ec8f65)

Screenshot of generated plot

![13](https://github.com/user-attachments/assets/74e861b1-8dec-451f-b251-462e081845d7)

Rise transition time calculation

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

20% Screenshots

![14](https://github.com/user-attachments/assets/cb992d7d-885e-4a17-a057-129e50112461)

![15](https://github.com/user-attachments/assets/eda7f6bc-9728-4f0c-8e76-2676b22b779c)

80% Screenshots

![16](https://github.com/user-attachments/assets/c47409c5-6680-4ed7-ba56-6ace5daa61a5)

![17](https://github.com/user-attachments/assets/9540a801-0c9d-460d-8b59-6e5e685f2bc6)

```math
Rise\ transition\ time = 2.24638 - 2.18242 = 0.06396\ ns = 63.96\ ps
```
Fall transition time calculation

```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```
Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Link to Sky130 Periphery rules: [https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html](https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html)

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```bash
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
```
Screenshots of commands run

![18](https://github.com/user-attachments/assets/4fc53c20-8138-426d-aa96-e61391f30146)

![19](https://github.com/user-attachments/assets/3592b8dc-844d-4079-b420-54acc2655287)

Screenshot of .magicrc file

![20](https://github.com/user-attachments/assets/2f8988e8-2b68-4699-a11b-37c80d13f61e)

Incorrectly implemented poly.9 simple rule correction



Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u

![image](https://github.com/user-attachments/assets/d3fb46b5-f512-4702-aa3f-b17aef2f73f1)

![image](https://github.com/user-attachments/assets/1806f7c4-2515-4c28-9e50-3c412464b40d)

Below are the commands  that need to be inserted in sky130A.tech file to update drc and fix this error

![image](https://github.com/user-attachments/assets/9a4b528e-d2a9-4af2-a7a0-a61ba46f634e)

![image](https://github.com/user-attachments/assets/96792114-34ca-4f7c-b2a0-5c1705958299)

Commands to run in tkcon window
```
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

![image](https://github.com/user-attachments/assets/27812378-5d66-4969-984c-643d7e810c42)

Incorrectly implemented difftap.2 simple rule correction




Incorrectly implemented in tkcon window

![image](https://github.com/user-attachments/assets/b235386e-aa46-49cc-8b74-dbcfabeb9f2e)


Commands to run in tkcon window
```
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented showing no errors found 

![image](https://github.com/user-attachments/assets/deaff09a-d890-4403-a293-5be3e9993a41)


## Day 4
Pre-layout timing analysis and importance of good clock tree
Fix up small DRC errors and verify the design is ready to be inserted into our flow.

Conditions to be verified before moving forward with custom designed cell layout:
* Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
* Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
* Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.

Commands to open the custom inverter layout

```bash
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_bibinv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd



Commands for tkcon window to set grid as tracks of locali layer

```tcl
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```
![1](https://github.com/user-attachments/assets/befcc50d-db8d-4892-9177-96eda7c441c9)

Condition  verified

![2](https://github.com/user-attachments/assets/2eb7e876-0fb3-4852-86e2-a327864523e2)

 Save the finalized layout with custom name and open it.

 Command for tkcon window to save the layout with custom name

```tcl
# Command to save as
save sky130_bibinv.mag
```

Command to open the newly saved layout

```bash
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_bibinv.mag &
```
![4](https://github.com/user-attachments/assets/d6250212-de84-4653-9acf-67ff6b90d981)

Generate lef from the layout.

Command for tkcon window to write lef

```tcl
# lef command
lef write
```
![5](https://github.com/user-attachments/assets/0118fc1c-710d-4783-8122-a20fe225fd39)

Screenshot of newly created lef file

![6](https://github.com/user-attachments/assets/798349b1-2baf-4282-b272-f8b641f03469)

Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

![7](https://github.com/user-attachments/assets/b61c931a-ec02-4259-8d7a-6685e51b3c1c)

Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow

```tcl
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory

![8](https://github.com/user-attachments/assets/c3199020-cd54-40e5-893c-bd9dd6cad30a)

Run openlane flow synthesis with newly inserted custom inverter cell.

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshots of commands run

![9](https://github.com/user-attachments/assets/6bc5c4bc-5dea-41be-b2b1-9ea19560bf3e)

![10](https://github.com/user-attachments/assets/ece2d788-5a9b-463e-a47c-2bcee698f522)

![11](https://github.com/user-attachments/assets/887027b4-2e09-4322-ab07-9878ca93eb86)

![12](https://github.com/user-attachments/assets/eeab2481-6b0e-4139-af09-27d0b0c5bfc1)

Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

Noting down current design values generated before modifying parameters to improve timing

![12](https://github.com/user-attachments/assets/eeab2481-6b0e-4139-af09-27d0b0c5bfc1)

Commands to view and change parameters to improve timing and run synthesis

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 15-11_03-56 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
![13](https://github.com/user-attachments/assets/8bfc49d3-628a-41c6-ab44-108ba880fa75)

![14](https://github.com/user-attachments/assets/3bbbb5be-2985-4f98-bad1-3ad8b2d1174e)

![15](https://github.com/user-attachments/assets/c79a579b-ace8-4eef-aee4-eec09df6a841)


Comparing to previously noted run values  worst negative slack has become 0

Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command

```tcl
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```

![16](https://github.com/user-attachments/assets/9b77893c-3d42-4f18-96de-a4ab25cf2e4f)

![17](https://github.com/user-attachments/assets/3449d8a3-fbed-40e2-8a9b-7078e1b83de6)

Now that floorplan is done we can do placement using following command

```tcl
# Now we are ready to run placement
run_placement
```
![18](https://github.com/user-attachments/assets/756bc54a-0b84-4520-a2d0-4ae3d09a49ab)

![19](https://github.com/user-attachments/assets/4de413b4-056e-4085-ab70-442b39cbf7a2)

Screenshot of placement def in magic

![20](https://github.com/user-attachments/assets/05918152-735e-48ed-bebc-6552da494189)

![21](https://github.com/user-attachments/assets/d83c6a49-faf9-44f6-8308-47e0da588539)

![22](https://github.com/user-attachments/assets/35206639-5402-458b-b9b8-b6f5c91a4045)

Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis 
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
![23](https://github.com/user-attachments/assets/4a559e60-1ad3-4a9a-bb5f-1df070695bc0)

![24](https://github.com/user-attachments/assets/1a1fdaaa-b079-4d1d-bb74-502f25397522)

![30a](https://github.com/user-attachments/assets/a4b644bb-2c0b-4363-b7b3-9c66c701450d)


Newly created pre_sta.conf for STA analysis in openlane directory

![31a](https://github.com/user-attachments/assets/4b81d7c3-117a-4114-a246-c12d4b4dce49)

Newly created `my_base.sdc` for STA analysis in `openlane/designs/picorv32a/src` directory based on the file `openlane/scripts/base.sdc`

![34a](https://github.com/user-attachments/assets/a3989dbc-f9ee-47de-9fc6-228b83e7bcec)


Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```
![32a](https://github.com/user-attachments/assets/45835de2-b250-4836-ae08-a99f11994f1b)

![33a](https://github.com/user-attachments/assets/b9112b9a-aa5c-4acb-807f-aba8b55ef9b2)

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis 

```tcl
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 16-11_00-58 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

![36a](https://github.com/user-attachments/assets/28641c2a-f4e1-4a8e-9102-4f9cbd823be4)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```
![37a](https://github.com/user-attachments/assets/9d5a1b4e-ebb5-4f28-bcbe-91489139e4cf)

Make timing ECO fixes to remove all violations.

OR gate of drive strength 2 is driving 4 fanouts

![38a](https://github.com/user-attachments/assets/7a1bfb6c-d69a-4a55-a729-52d13ad51c3e)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![39a](https://github.com/user-attachments/assets/50f4f9cd-65a5-4aef-aa2a-3d05ab9fa759)

![40a](https://github.com/user-attachments/assets/5279bfad-be28-410c-8bda-9b01518659ac)

OR gate of drive strength 2 is driving 4 fanouts

![41a](https://github.com/user-attachments/assets/b08d3a0a-b578-427b-8d6e-4ecf3b736ecd)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

![42a](https://github.com/user-attachments/assets/c64567ed-1638-4015-9425-fff8d537f54d)

![43a](https://github.com/user-attachments/assets/3c0b4530-4169-4ace-b4c5-3b473fd3c819)

OR gate of drive strength 2 driving OA gate has more delay

![44a](https://github.com/user-attachments/assets/2d700afb-9263-40d6-9f9d-ee5dc25a955b)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![45a](https://github.com/user-attachments/assets/78c760c2-e35e-489e-8619-3774879c74d7)

![46a](https://github.com/user-attachments/assets/d5ebcaa3-3d91-4f54-84be-215d5505f629)

OR gate of drive strength 2 driving OA gate has more delay

![47a](https://github.com/user-attachments/assets/535b2db3-2416-4d7a-8fa9-a4e9169fe71b)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![48a](https://github.com/user-attachments/assets/142edd30-1b63-425c-938d-e3af79090d90)

![49a](https://github.com/user-attachments/assets/dfb1083e-ef1d-47e6-91ba-b5e28d60a7dd)

Commands to verify instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

```tcl
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```
![50a](https://github.com/user-attachments/assets/ac51d9b6-5c91-4b17-8467-55026ce4e68e)

![51a](https://github.com/user-attachments/assets/721d1e17-35f7-4611-b5f5-8d75d2c36e44)

Screenshot of replaced instance

![52a](https://github.com/user-attachments/assets/310929ce-266f-46b5-9cd8-88bce6081ea4)

We started ECO fixes at wns -23.9000 and now we stand at wns -22.6173 we reduced around 1.2827 ns of violation.

Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use `write_verilog` and overwrite the synthesis netlist but before that we are going to make a copy of the old  netlist

Commands to make copy of netlist

```bash
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_03-37/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```
![53a](https://github.com/user-attachments/assets/2e81765e-3136-4ede-b8d4-d6f6f44be538)

Commands to write verilog

```tcl
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_03-37/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```
![54a](https://github.com/user-attachments/assets/86d65c29-4cdb-40a8-a98a-1e845b79a3a3)

Verified that the netlist is overwritten by checking that instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

![55a](https://github.com/user-attachments/assets/5ad94c55-1c79-41d7-a66d-0596368d0c97)

Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 16-11_03-37 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```
![56a](https://github.com/user-attachments/assets/2fac5058-87de-4857-b38c-450abcb18005)

![57a](https://github.com/user-attachments/assets/b2bb3ad5-ee2a-4982-8afa-51bfeee07900)

![58a](https://github.com/user-attachments/assets/893d5772-c739-4390-af0d-585fb43d169a)

![59a](https://github.com/user-attachments/assets/5df2d328-bbe3-42ac-841b-7cee4b093c79)

![60a](https://github.com/user-attachments/assets/be052ef9-9055-4623-812d-034264313bd2)

 Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/16-11_03-37/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/16-11_03-37/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/16-11_03-37/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![61a](https://github.com/user-attachments/assets/e65d600f-8943-4fbf-8380-e243d0174697)

![62a](https://github.com/user-attachments/assets/122c1e9f-adf2-41d6-a32f-84616791ee55)

![63a](https://github.com/user-attachments/assets/9abdbbff-e39a-4f62-9343-f7080cf4de76)

![64a](https://github.com/user-attachments/assets/52860535-91c3-416d-8332-4e6a6709e63c)

Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing `CTS_CLK_BUFFER_LIST`

```tcl
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/16-11_03-37/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/16-11_03-37/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/16-11_03-37/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```

Screenshots of commands run and timing report generated

![65a](https://github.com/user-attachments/assets/44e99fc5-5ff2-42a2-9b1b-09f5eb1b5ffd)

![66a](https://github.com/user-attachments/assets/ff1d2818-85af-4675-809c-2a36cb2eef62)

![67a](https://github.com/user-attachments/assets/07dc0f36-eb17-44de-b9da-85ab7ad5889b)

![68a](https://github.com/user-attachments/assets/1cf585dd-c119-4dd2-b3be-e3172dea4dae)

# Day 5
Final steps for RTL2GDS using tritonRoute and openSTA
Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 
```
![1](https://github.com/user-attachments/assets/9d5ede8f-2bdd-4fbf-a1e6-a7dd18875f7d)

![2](https://github.com/user-attachments/assets/db7e4c79-8dd9-43b9-b324-11c01145289f)

Commands to load PDN def in magic in another terminal

```bash
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_09-23/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```
![4](https://github.com/user-attachments/assets/4c0dfa7d-b445-4f64-b713-19cf2227a121)


![3](https://github.com/user-attachments/assets/e539573f-c0f0-400a-92a2-3ea7054ffa3b)

![5](https://github.com/user-attachments/assets/9d4d942f-a03e-4922-aec0-69709a041aac)

![6](https://github.com/user-attachments/assets/e6fe15a6-b174-4dd7-9736-25c0a077c0ed)


Perfrom detailed routing using TritonRoute and explore the routed layout.

Command to perform routing

```tcl
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```
![7](https://github.com/user-attachments/assets/4a01e2d2-80f8-48a6-9e1f-56285b2b32c8)

![8](https://github.com/user-attachments/assets/4222858a-ac4a-4410-ac68-21163538c0bf)

![9](https://github.com/user-attachments/assets/ace3bc30-0948-42aa-a792-2c2d5782ba12)

![10](https://github.com/user-attachments/assets/b243537b-1775-4997-975c-91a12da10e84)

![11](https://github.com/user-attachments/assets/895c53c3-e9bc-4117-8bd3-e0adef80d4e5)

![12](https://github.com/user-attachments/assets/b907f11c-4f09-4d71-9833-465652866eed)

Commands to load routed def in magic in another terminal

```bash
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_09-23/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
![14](https://github.com/user-attachments/assets/8c012e06-b917-45bd-a199-9e415abe5051)

![13](https://github.com/user-attachments/assets/79a5bc9d-7cbe-4987-8b75-5b4b5eac5897)

![15](https://github.com/user-attachments/assets/a5d11550-e528-4868-a844-8416f634f57d)

![16](https://github.com/user-attachments/assets/dad312a4-7941-4887-8142-b950ce06105e)

Screenshot of fast route guide present in `openlane/designs/picorv32a/runs/26-03_08-45/tmp/routing` directory

![17](https://github.com/user-attachments/assets/f94eb38c-eb2b-494f-b5d5-7a8bfada4094)

 Post-Route parasitic extraction using SPEF extractor.

Commands for SPEF extraction using external tool

```bash
# Change directory
cd Desktop/work/tools/SPEF_EXTRACTOR

# Command extract spef
python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_09-23/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_09-23/results/routing/picorv32a.def
```
Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/16-11_09-23/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/16-11_09-23/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/16-11_09-23/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/16-11_09-23/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```
![18](https://github.com/user-attachments/assets/a3d5a371-2648-411d-b006-9e40b21f8fa5)

![19](https://github.com/user-attachments/assets/980da7ef-6460-4789-b3e5-fab31739337c)

![20](https://github.com/user-attachments/assets/fdcf84b2-2653-4342-a061-ff64c4cb740a)

![21](https://github.com/user-attachments/assets/0977a0d5-859e-445c-8fef-2f3f5f556730)

![22](https://github.com/user-attachments/assets/2ac58299-612e-4b84-b303-8e6fe92798b3)


## Task-14: OpenRoad Physical Design

#### Path to Zetta-Scale Computing

**Introduction:**

- **Bombe:** The Bombe was an electro-mechanical machine designed during World War II to decrypt German Enigma-encrypted messages. It was refined and built by Alan Turing and Gordon Welchman at Bletchley Park, UK. The Bombe systematically tested possible rotor settings of the Enigma machine by exploiting known plaintext patterns. Its logical operations helped narrow down the vast number of possible keys, significantly accelerating the decryption process. The Bombe played a critical role in the Allied war effort.

- **ENIAC (Electronic Numerical Integrator and Computer):** It was developed during World War II by John Presper Eckert and John Mauchly at the University of Pennsylvania, was the first general-purpose, fully electronic digital computer. Completed in 1945, it was designed to compute artillery firing tables for the U.S. Army. ENIAC used vacuum tubes instead of mechanical or electromechanical components. However, it lacked a stored-program capability, requiring manual reconfiguration for each new task. ENIAC demonstrated the immense potential of electronic computing for large-scale numerical problems.

- **EDVAC (Electronic Discrete Variable Automatic Computer):** EDVAC, also developed by Eckert and Mauchly with conceptual input from John von Neumann, was one of the first computers to implement the stored-program concept. Completed in 1949, EDVAC represented a significant improvement over ENIAC by using binary representation instead of decimal and storing both data and instructions in memory. This innovation simplified programming and laid the groundwork for the modern von Neumann architecture.

**50 Years of Microprocessor Trend Data:**

![image](https://github.com/user-attachments/assets/04124b15-8ba2-4cd9-add6-fd003838fe6c)

**The Key metrics are:**

- **Transistors (Orange Triangles):** The number of transistors on a microprocessor chip (in thousands) has increased exponentially, following Moore's Law, which predicts a doubling approximately every two years. This growth enabled more complex and capable processors, reaching the range of billions of transistors by the 2020s.
- **Single-Thread Performance (Blue Circles):** It is measured using SpecINT. It indicates the computational ability of a single processor core. Performance grew steadily due to improvements in architecture, instruction-level parallelism, and clock speeds, but the growth rate slowed post-2005 due to physical limitations like power and heat.
- **Frequency (Green Diamonds):** Processor clock speed (in MHz) rose steadily until the early 2000s but then stagnated as increasing clock speeds became inefficient due to heat dissipation issues.
- **Typical Power (Red Triangles):** Power consumption increased with transistor density and frequency, becoming a critical design challenge around the mid-2000s.
- **Number of Logical Cores (Black Dots):** The transition to multi-core processors gained momentum in the mid-2000s as a response to the stagnation in single-thread performance. By increasing the number of cores, processors enabled more efficient parallel processing, leading to significant improvements in overall performance

**Key Milestones**

- **iPhone Release (~2007):** Signals the emergence of mobile computing, where power efficiency became as crucial as performance. This catalyzed innovations in low-power processor designs.
- **Datacenter-Scale Computing (Post-2010):** Marks the rise of cloud computing and large-scale data centers, where energy efficiency, scalability, and parallelism became central concerns.

**Path to zetta-scale computing**

![image](https://github.com/user-attachments/assets/7f0a1590-b0ca-4d90-8804-381b30bee78a)

The path to zetta-scale computing, tracing the evolution of computing performance (measured in FLOPS—floating-point operations per second) from the gigascale era in 1984 to the projected zettascale by 2035.

**Key Performance Levels**

- **Gigascale (10⁹ FLOPS):** The starting point in 1984, marking the capability of early supercomputers.
- **Terascale (10¹² FLOPS):** Achieved around 1997, a significant milestone where systems like Jaguar (Cray XT5) delivered teraflop performance with power consumption of 7 MW.
- **Petascale (10¹⁵ FLOPS):** Achieved in 2008 with systems like Titan (Cray XK6) at 27 petaflops, consuming 9 MW. This milestone represents the era of petascale high-performance computing (HPC).
- **Exascale (10¹⁸ FLOPS):** Reached by systems like Frontier (Cray Shasta) in 2021, delivering 1.5 exaflops using 4 AMD GPUs and 1 AMD CPU, consuming 29 MW of power. Exascale computing enables highly detailed simulations and large-scale AI workloads.
- **Zettascale (10²¹ FLOPS):** Projected to be achieved by around 2035. At this scale, systems will handle unprecedented computational workloads, such as advanced climate modeling, AI, and large-scale simulations. Power consumption is estimated to range between 50-100 MW for a single zettascale machine.

**CMOS Evolution and Next-Gen Candidates**

![image](https://github.com/user-attachments/assets/b621caad-384e-4c67-bb01-4504d153230a)

This diagram illustrates the evolving landscape of CMOS (Complementary Metal-Oxide-Semiconductor) technology and highlights emerging materials, structures, and processes being explored for next-generation semiconductor devices. These innovations aim to address the challenges of scaling CMOS technology down to the 1nm node and beyond.


- **Channel Material**
  - **Current Trends**: 
    - Silicon (Si) is the primary material used for the channel in traditional CMOS transistors, with **strained SiGe** (Silicon-Germanium) being used in some high-performance applications to enhance carrier mobility.
  
  - **Future Materials**: 
    - **2D materials** such as MoS₂ (Molybdenum Disulfide) are being explored due to their potential for better electrical characteristics at smaller scales.
    - **Germanium (Ge)** is gaining interest as it offers higher electron mobility, which could significantly boost transistor performance at small nodes.

- **Patterning**
  - **Current Techniques**: 
    - **Deep Ultraviolet (DUV)** lithography is the most commonly used technique for defining transistor features, with **ArF (Argon Fluoride)** and **KrF (Krypton Fluoride)** lasers operating at different wavelengths.
  
  - **Next-Gen**: 
    - **Extreme Ultraviolet (EUV)** lithography is expected to be a key technology for sub-7nm nodes. **High-NA (Numerical Aperture) EUV** will further improve the resolution for even smaller transistor nodes, pushing the boundaries of Moore's Law.

- **Gate Stack Material**
  - **Current Materials**: 
    - **High-K metal gates (HKMG)** are used in the gate stack of modern FETs to reduce gate leakage current and improve switching performance.
  
  - **Next-Gen Candidates**:
    - **NC-FET (Negative Capacitance FET)**: This is a promising transistor design that leverages ferroelectric materials to reduce power consumption by enabling lower voltage operation.
    - **TFET (Tunnel FET)**: TFETs use quantum tunneling to switch on and off, offering a significant reduction in power consumption compared to conventional FETs, especially for low-power applications.

- **Interconnection Material**
  - **Current Materials**: 
    - **Copper (Cu)** is the primary material used for interconnects due to its low resistivity, which helps in minimizing power loss and delays in transistor connections.
  
  - **Next-Gen Materials**:
    - **Ruthenium (Ru)** and **Compound metals** are being investigated for their potential to reduce resistance and improve performance in ultra-small transistors.
    - **Topological semi-metals** may offer unique properties, such as lower resistivity and increased performance at the atomic scale.


- **Device Structure**
  - **Current Architectures**: 
    - **FinFET** and **planar** transistors are used to maintain performance at smaller nodes. FinFETs, in particular, help improve control over short-channel effects by using a 3D structure.
  
  - **Next-Gen Architectures**:
    - **3DS-FET (3D Stacked FET)**: These are three-dimensional transistors where multiple layers of devices are stacked vertically, reducing footprint and improving performance.
    - **MBC-FET (Multi-Bridge Channel FET)**: This structure aims to enhance drive current by creating multiple channels within the same device.
    - **VFET (Vertical FET)**: VFETs utilize vertical channels to improve density and reduce power consumption.

- **Design Co-Optimization**
  - **DTCO (Design-Technology Co-Optimization)**: 
    - DTCO focuses on integrating new design techniques with advanced process technologies to maximize chip performance, often involving **backside interconnects (BSI)**, where interconnections are made at the back of the wafer for improved signal integrity and reduced latency.
  
  - **STCO (System-Technology Co-Optimization)**: 
    - This approach involves optimizing both the system architecture and the underlying technology. One example is the use of **chiplets**, which allow for modular, customized designs by integrating multiple smaller chips into one package, offering flexibility and reducing the complexity of scaling single-chip designs.

#### FinFETs

![image](https://github.com/user-attachments/assets/de21941f-7456-4522-b07f-a365cf9fe9b0)

This diagram illustrates the evolution of transistor technology from planar to more advanced architectures like FinFET and Gate-All-Around (GAA):

1. **Planar Transistor (Traditional)**:
   - Early transistor design with a flat channel and gate structure.
   - The gate controls the channel from one side only, leading to limited performance as scaling continues.

2. **FinFET (2011)**:
   - The channel is shaped like a vertical fin, allowing the gate to wrap around three sides of the channel.
   - Provides better control over the channel, reducing leakage and improving performance at smaller sizes.

3. **Gate-All-Around (GAA) Transistor (2025?)**:
   - The gate completely surrounds the channel, typically implemented using stacked nanosheets or nanowires.
   - Offers even better control over the channel compared to FinFET, allowing higher performance and efficiency with continued scaling.

Each step improves drive current capability and enhances control over the transistor's on/off states, critical for power efficiency and miniaturization in modern electronics.

**Why FinFETs and Gate-All-Around Transistors?**

![image](https://github.com/user-attachments/assets/067b362e-bd68-40e4-b83c-60f2c3ef5797)

This diagram explains the advantages of FinFETs and Gate-All-Around (GAA) transistors compared to traditional planar structures:

 1. **Planar Transistors:**
   - **Challenges:**
     - Sub-channel leakage occurs where current leaks underneath the gate.
     - Results in reduced efficiency.
     - Increases power consumption.

2. **FinFET Transistors:**
   - The gate wraps around the channel (fin) on three sides, providing better control over the channel.
   - **Benefits:**
     - Reduces sub-threshold leakage.
     - Enhances drive current (\(I_{ON}\)).
     - Allows a smaller transistor area while maintaining high performance.

3. **Gate-All-Around (GAA) Transistors:**
   - The gate completely surrounds the channel, offering superior electrostatic control.
   - **Advantages:**
     - Improves short-channel performance by reducing drain capacitance and enhancing gate capacitance.
     - Improves scaling efficiency as indicated by the formula \(S \propto (1 + C_d / C_{ox})\).
     - Provides reduced sub-threshold slope and better performance at smaller scales.

4. **Graph Comparison:**
   - Illustrates the performance advantages of FinFETs and GAA over planar transistors.
   - Shows better efficiency and reduced sub-threshold slope as dimensions shrink.

![image](https://github.com/user-attachments/assets/29504769-f396-4838-8ebb-abacfaf8a27f)

**Reduced Leakage:** Tri-Gate transistors exhibit significantly lower leakage current compared to planar transistors at the same gate voltage. Lower leakage results in both reduced off-current at the same on-current and lower power dissipation.

**Higher Drive Current:** Tri-Gate transistors provide higher drive current compared to planar transistors at the same off-current. This results in improved circuit performance and greater efficiency in modern electronic applications.

#### FEOL Innovations:

FEOL refers to the initial stages of semiconductor manufacturing where the active devices (e.g., transistors) are built on the silicon wafer. It involves creating components such as transistors, capacitors, and isolation structures before metal interconnects are added. FEOL Innovations help drive Moore's Law forward by enabling smaller, more efficient, and more powerful transistors.

**CMOS Technology Inflection Points**

![image](https://github.com/user-attachments/assets/66560a1e-fd66-40dc-94ed-9de5938f045c)

1. **Dennard Scaling**:
   - States that power density remains constant as transistors shrink.
   - Initially allowed voltage scaling with smaller gate lengths, shown in the bottom-left graph.

2. **Technology Nodes and Innovations**:
   - **~1 µm ("End of Scaling")**: Start of CMOS miniaturization.
   - **180 nm (Voltage Scaling)**: Start of drive voltage reduction.
   - **130 nm (Cu BEOL)**: Introduction of copper interconnects for better conductivity.
   - **90 nm (Uniaxial Strained Si NMOS)**: Strained silicon enhances electron mobility.
   - **65 nm (eSiGe CVD ULK)**: Embedded SiGe improves PMOS performance.
   - **45 nm (HK-first MG-last)**: High-k dielectrics and metal gates reduce leakage and improve gate control.
   - **32 nm (HKMG with Raised S/D NMOS)**: Advanced HKMG implementation and raised source/drain regions.

3. **SEM Images**

- **Left Image:** Shows the cross-sectional view of a transistor structure with High-k materials and embedded SiGe (Silicon-Germanium).It has high-k dielectric and metal gates are used to improve performance. SiGe regions enhance PMOS performance by applying strain to the silicon channel.

- **Right Image:** Demonstrates the raised source/drain (S/D) regions and gate channel in PMOS transistors at smaller nodes.

4. **Drive Voltage Scaling Graph (Bottom-left):** The graph shows the relationship between gate length (x-axis, logarithmic scale) and drive voltage (y-axis, logarithmic scale). The Ideal scaling behavior indicates that the voltage decreases linearly with shrinking gate length. Red and green markers show practical trends for low-power and high-performance devices, which deviate from ideal scaling due to challenges like leakage currents and increased power density.

![image](https://github.com/user-attachments/assets/10c7507f-19a8-422c-9ef3-4f044e900766)

**Key Technology Nodes and Innovations**

- **22 nm**:
  - Introduction of **FinFET (Tri-Gate)** transistors, which reduce leakage and improve gate control.
  - Use of **self-aligned contacts (SAC)** and **copper interconnects (Co+Cu BEOL)**.

- **14 nm**:
  - Transition to **unidirectional metal routing** for better density.
  - Implementation of **SADP (Self-Aligned Double Patterning)** and **SDB (Single Diffusion Break)** for precise layout.

- **10 nm**:
  - Adoption of **advanced patterning techniques** such as:
    - **SA-SDB** (Self-Aligned SDB)
    - **LELELE** (Litho-Etch-Litho-Etch-Litho-Etch)
    - **SAQP (Self-Aligned Quadruple Patterning)** for tighter geometries.

- **7 nm**:
  - Introduction of **Extreme Ultraviolet Lithography (EUV)** to simplify the patterning process and reduce overlay errors.

- **5 nm**:
  - Integration of **SiGe (Silicon-Germanium) channels** for PMOS to enhance hole mobility.
  - Use of **EUV SA-LELE** (Self-Aligned Litho-Etch-Litho-Etch).

- **3 nm / 2 nm / 1.4 nm**:
  - Transition to **Gate-All-Around (GAA)** nanosheet transistors for improved electrostatic control.
  - GAA stacks nanosheets or nanowires horizontally to maximize current drive.

- **Sub-1 nm**:
  - Development of **CFET (Complementary FET)**, which vertically stacks NMOS over PMOS to save area.
  - Use of **2D materials**, such as **MoS₂**, for atomic-scale channel thickness in **2D FETs**.

![image](https://github.com/user-attachments/assets/a8ad69be-9750-44f0-97b6-c39f1b58e18c)

The image illustrates how Samsung has scaled down the size of transistors in their successive generations of nodes (10nm, 8nm, 7nm, and 5nm) using a technique called Fin Depopulation. In FinFET transistors, the "fin" is the vertical channel that carries the current. Fin Depopulation involves reducing the number of fins per transistor while keeping the fin width constant. This allows for smaller transistors without compromising performance.

- 10nm (HD): The transistor has a fin height of 420nm and uses 10 fins.
- 8nm (UHD): The fin height is reduced to 378nm, and the number of fins is decreased to 9.
- 7nm (HD): The fin height remains at 27nm, but the number of fins is further reduced to 8.
- 5nm (UHD): The fin height is maintained at 27nm, and the number of fins is decreased to 7.

![image](https://github.com/user-attachments/assets/c6bc381c-f5de-4839-98a9-e61f56b61622)

- **Double Diffusion Break (DDB)**: Double Diffusion Break (DDB) involves creating a gap between the source and drain regions of a transistor. This gap is filled with an insulating material, which reduces the effective width of the transistor. By doing so, DDB enables the design of smaller cell sizes, allowing for higher transistor density and improved scalability. A cross-sectional view of a transistor with DDB highlights the insulating gap between the source and drain regions.

- **Single Diffusion Break (SDB)**: Single Diffusion Break (SDB) is similar to DDB but less aggressive. It involves introducing a gap on only one side of the transistor. This approach provides a balanced trade-off between size reduction and maintaining transistor performance. A cross-section of a transistor with SDB highlights the gap on one side, showcasing its simplicity compared to DDB.

- **Contact Over Field Gate (COFG)**: Contact Over Field Gate (COFG) places the gate contact directly over the field oxide region of a transistor. This design reduces lateral spacing between adjacent transistors, enabling smaller cell sizes without significant performance loss. A cross-sectional representation of a transistor with COFG illustrates the positioning of the gate contact over the field oxide.

- **Contact Over Active Gate (COAG)**: Contact Over Active Gate (COAG) is a more aggressive technique than COFG. Here, the gate contact is placed directly over the active gate region of the transistor. This approach enables even smaller cell sizes and higher transistor density, which are critical for advanced semiconductor nodes. A cross-sectional image of a transistor with COAG highlights the gate contact placement over the active gate.

- **Back-Side Power Delivery Network (BS-PDN)**: The Back-Side Power Delivery Network (BS-PDN) is an innovative approach where power supply rails are routed on the backside of the chip. This method reduces the height of the standard cell, creating space for more transistors and improving overall transistor density. Additionally, it enhances power delivery efficiency and reduces resistance, which is crucial for high-performance applications. A schematic of a standard cell with BS-PDN illustrates the positioning of power rails on the backside of the chip.

![image](https://github.com/user-attachments/assets/d8288063-a78a-40cb-a80b-7f9fe8d351bc)

- **Planar Technology**: In early planar technology nodes (100nm and above), the Vt variability is significantly high, around 130mV. This is due to various factors like process variations, temperature fluctuations, and line-edge roughness.

- **FinFET Technology**: With the advent of FinFET technology (around 22nm), the Vt variability reduces significantly to around 14mV. This improvement is attributed to the better control over the channel length and width in FinFETs compared to planar transistors.

- **NW Technology (Nanowire)**: In the latest nanowire technology (14nm and below), the Vt variability is even lower, around 7mV. This further reduction is due to the precise control over the nanowire dimensions and the reduced impact of process variations.

![image](https://github.com/user-attachments/assets/43ec16fc-dac1-4ac4-9492-ef7413e39ef6)

**Planar MOSFETs**  
Planar MOSFETs, the traditional architecture, have a simple structure where the gate sits above the channel. In this design, the contact width (\(W_C\)) and gate width (\(W_G\)) are nearly equal, resulting in a ratio of \(W_C / W_G \approx 1\). This leads to a low parasitic resistance, with \(R_{EXT}\) being much smaller than \(R_{ch}\) (\(R_{EXT} / R_{ch} < 1\)). As a result, planar MOSFETs suffer minimal performance degradation due to parasitic resistance.

**FinFETs**  
FinFETs, a 3D transistor design, introduce vertical fins with the gate wrapping around them for improved control. However, the effective contact width decreases relative to the gate width, leading to \(W_C / W_G \approx 1/3\). Consequently, the parasitic resistance becomes comparable to the channel resistance (\(R_{EXT} / R_{ch} \approx 1\)), which begins to impact the performance of the device as it scales.

**Gate-All-Around (GAA) FETs**  
Gate-All-Around (GAA) FETs, which use nanosheets or nanowires, offer even better electrostatic control by fully surrounding the channel with the gate. However, the contact width further decreases compared to the gate width, resulting in \(W_C / W_G \approx 1/6\). This causes a significant increase in parasitic resistance, with \(R_{EXT}\) being approximately three times the channel resistance (\(R_{EXT} / R_{ch} \approx 3\)). While GAA FETs improve transistor density, the higher parasitic resistance becomes a challenge for maintaining performance.

**Complementary FETs (CFETs)**  
Complementary FETs (CFETs) take transistor stacking to the next level by vertically integrating NMOS and PMOS transistors. This approach maximizes space efficiency in advanced nodes but inherits the high parasitic resistance of GAA FETs. With \(W_C / W_G\) remaining small, the \(R_{EXT} / R_{ch}\) ratio is around 3, posing similar challenges to those faced by GAA FETs.

**Explanation of Parasitic Resistance**

![image](https://github.com/user-attachments/assets/6ab0011f-36de-4821-ab59-74fa2ce2beda)

The image highlights the breakdown of parasitic resistance (\(R_{EXT}\)) and approaches for reducing it in transistors. Here is a detailed explanation:

1. **Components of Parasitic Resistance (\(R_{EXT}\))**
The leftmost diagram illustrates the various contributors to \(R_{EXT}\) in a transistor:
- **\(R_{CA-BEOL}\)**: Resistance from the contact in the Back-End-Of-Line (BEOL).
- **\(R_{CA}\)**: Resistance at the contact area.
- **\(R_{CA-TS}\)**: Resistance at the contact to the transition structure.
- **\(R_{TS}\)**: Resistance in the transition structure.
- **\(R_{MOL}\)**: Middle-Of-Line resistance (includes lateral and vertical contributions).
- **\(R_C\)**: Contact resistance at the metal-semiconductor interface.
- **\(R_{EPI}\)**: Epitaxial layer resistance (contributes to current spreading).
- **\(R_{FEOL}\)**: Front-End-Of-Line resistance from the source/drain extensions.

2. **Initial vs. Improved \(R_{EXT}\) Breakdown**
The two pie charts in the center show the contributions of different resistance components for NFETs and PFETs before and after improvements:
- **NFET**:
  - **Initial**: Majority of \(R_{EXT}\) comes from \(R_C\) (63%) and \(R_{CA-BEOL}\) (31%).
  - **Improved**: Significant reduction in \(R_C\) (48%) and \(R_{CA-BEOL}\) (12%).
- **PFET**:
  - **Initial**: \(R_{FEOL}\) (50%) and \(R_C\) (45%) dominate.
  - **Improved**: Major reduction in \(R_{FEOL}\) (78%) and \(R_C\) (16%).

3. **Improving Ohmic/Tunneling Contacts**
The right section discusses methods to improve the metal-semiconductor interface:
- **Key Objectives**:
  - **Low Schottky Barrier Height (SBH)** (\(\phi_b\)): Reduces the energy barrier for carrier injection, enabling better contact conductivity.
  - **High Doping Concentration (\(N_d\))**: Increases carrier density at the interface, reducing contact resistance.
- **Equation for Specific Contact Resistivity (\(\rho_c\))**:
  \[
  \rho_c \propto \exp\left(\frac{2\phi_b}{\hbar} \sqrt{\frac{\epsilon_s m_x}{N_d}}\right)
  \]
  This equation shows how lowering \(\phi_b\) and increasing \(N_d\) can reduce \(\rho_c\).

- **Metal-Semiconductor Energy Diagram**:
  - The energy diagram shows how a reduction in \(\phi_b\) (Schottky Barrier Height) facilitates easier carrier injection from the metal to the semiconductor.

![image](https://github.com/user-attachments/assets/ed9743a8-c9f0-43d5-9ccd-4b239f8718ac)

The bar chart on the left shows how the composition of \(C_{eff}\) evolves from 22nm to 7nm technology nodes:

- At **22nm**, the dominant contributor to \(C_{eff}\) is \(C_{fr}\) (56%), while parasitic capacitances \(C_{pc-ca}\) (25%) and \(C_{g}\) (19%) contribute less.
- At **14nm** and **10nm**, parasitic capacitances (\(C_{pc-ca}\) and \(C_{fr}\)) start dominating, with \(C_{fr}\) decreasing to 38% and 25%, respectively, while \(C_{pc-ca}\) increases.
- At **7nm**, \(C_{g}\) becomes the most significant contributor (45%), with \(C_{pc-ca}\) and \(C_{fr}\) still present but reduced. This highlights the increasing impact of parasitic capacitance as node sizes shrink.

Plot Descriptions:

- The first scatter plot shows a reduction in normalized delay for a ring oscillator when using SiBCN spacers instead of SiN spacers, indicating improved performance.
- The second scatter plot demonstrates an 8% reduction in \(C_{eff}\) with SiBCN spacers, which corresponds to the delay improvement observed in the first plot.
- The rightmost figure shows the evolution of spacer materials from SiOCN to SiCO. This material transition aims to significantly reduce the gate-contact capacitance across nodes. At 14nm and beyond, low-\(k\) spacers improve performance by decoupling parasitic effects and maintaining capacitance at manageable levels.
- The bottom middle image shows a cross-sectional TEM view of a transistor with air spacers around the gate: i) Air, with its extremely low dielectric constant (\(k \approx 1\)), significantly reduces parasitic capacitance. The adjacent plot quantifies this improvement, showing a 15% reduction in \(C_{eff}\) when using air spacers compared to solid spacers.

![image](https://github.com/user-attachments/assets/848c85f2-a2d5-4872-9690-b6eaf1a11dd2)

**Key Properties of 2D Layered Materials (Compared to Silicon):**

- **Uniform Atomic Scale Thickness:** A single layer of MoS₂ is approximately 0.65 nm thick, offering an ideal thickness for scaling compared to silicon. 
- **Higher Effective Mass (\( m^* \)):** MoS₂ has an effective mass of about 0.55 times the mass of a free electron (\( m_0 \)), whereas silicon’s effective mass is around 0.22 \( m_0 \).
- **Bandgap:** Additionally, 2D materials like MoS₂ possess favorable bandgaps for electronic devices, with a monolayer bandgap of ~1.85 eV, which reduces to ~1.5 eV for a bilayer.

![image](https://github.com/user-attachments/assets/957f8ce6-cd3d-4fd3-bd3e-c99909752cdf)

1. **Transistor Scaling**:  
   - To achieve smaller gate lengths, devices must address various physical and material constraints to ensure reliable operation.

2. **Challenges for Scaling**:
   - **Direct Source-to-Drain Tunneling**: As the gate length decreases, electrons can tunnel directly from the source to the drain, bypassing the gate control. To mitigate this, materials with a high effective mass (\( m^* \)) are needed.
   - **Surface Roughness and Thickness Variations**: Variability at atomic scales can cause performance issues. Uniform, atomically thin materials are essential for minimizing such variations.
   - **Capacitance Ratios (\( C_D \) and \( C_{ox} \))**: The capacitance of the depletion region (\( C_D \)) must remain low relative to the gate oxide capacitance (\( C_{ox} \)) to improve gate control. Materials with a low in-plane dielectric constant (\( \epsilon \)) are necessary for this.

3. **Diagrams**:  
   - The left shows the transistor structure with key components like the source, drain, gate, oxide, and silicon substrate.
   - The right illustrates two scenarios:  
     a. *Thermionic Emission*: Electrons cross the energy barrier as intended.  
     b. *Direct Tunneling*: At extremely small gate lengths, electrons tunnel directly from source to drain, leading to leakage.

4. **Key Takeaway**:  
   - New channel materials, such as 2D materials, are required to overcome these challenges while maintaining high performance and scalability.

![image](https://github.com/user-attachments/assets/716a2a87-2051-4de1-be37-aa4f70f73fa0)

Concept of Direct Source-to-Drain Tunneling: As the gate length (\(L_G\)) in MOSFETs decreases, direct tunneling of electrons from the source to the drain becomes significant, leading to increased leakage currents. This leakage is influenced by material properties, such as the effective mass (\(m^*\)) and the bandgap (\(E_G\)).

A higher \(m^*\) in MoS₂ suppresses tunneling leakage compared to silicon. The graph shows the leakage current (\(I_{SD, \text{leak}}\)) as a function of gate length (\(L_G\)) for various channel thicknesses (\(T_{CH}\)). MoS₂ exhibits lower leakage at smaller gate lengths compared to silicon, achieving up to 100x reduction in leakage due to its higher \(m^*\), larger \(E_G\), and lower dielectric constant (\(\epsilon\)).

The superior performance of MoS₂ in minimizing leakage currents results in significant energy savings, making it a promising material for future transistor scaling.

![image](https://github.com/user-attachments/assets/333769a9-e265-4e58-ba3a-47dffc7ac60e)

The MoS₂ transistor with a 1 nm gate length represents a breakthrough in miniaturization, featuring a thin MoS₂ channel for its excellent electronic properties. A single-walled carbon nanotube (SWCNT) serves as the ultra-small gate electrode, while Zirconium Dioxide (ZrO₂) acts as a high-k dielectric, reducing leakage and ensuring precise control. Built on a SiO₂ substrate with an n⁺ silicon back gate, the transistor uses the CNT gate to deplete a small region of the MoS₂ channel, enabling efficient modulation. This innovative design showcases the potential of 2D materials and nanoscale gates in advancing transistor technology.

![image](https://github.com/user-attachments/assets/e2eef453-2d6f-4a72-ae50-5aa6d36bdfeb)

The slide illustrates the structure and fabrication of an All-2D MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor), where all key components, including the channel, gate, and contacts, are made using two-dimensional materials. This device leverages the exceptional properties of 2D materials to improve performance and scalability. Below is a breakdown of the key components and the fabrication process:

**Graphene Contacts (S, D, G):** Graphene is used as the source, drain, and gate electrodes. Its high conductivity and 2D nature make it ideal for ensuring low-resistance electrical contacts.
MoS₂ Channel:

**Molybdenum Disulfide (MoS₂)** serves as the semiconductor channel. MoS₂ is widely used in 2D MOSFETs due to its excellent on/off current ratio and atomic-scale thickness.
h-BN Dielectric:

**Hexagonal Boron Nitride (h-BN)** acts as the insulating dielectric layer. It is a 2D material with excellent insulating properties and high thermal stability, making it suitable for separating the graphene gate from the MoS₂ channel.
Si/SiO₂ Substrate:

The device is fabricated on a silicon dioxide (SiO₂) layer on top of a silicon substrate, which provides mechanical support and a global back gate.
Fabrication Process:

- A layer of graphene is deposited on the SiO₂ substrate, which will later serve as the gate electrode.
- Graphene is patterned to define the source and drain regions, leaving gaps for the channel.
- A monolayer of MoS₂ is transferred onto the patterned graphene, forming the channel region.
- An h-BN layer is added on top of the MoS₂ as the gate dielectric.
- A top layer of graphene is deposited and aligned as the gate electrode.
- The completed device is contacted using metallic electrodes (Ni/Au) for testing.

![image](https://github.com/user-attachments/assets/2fc6e2ec-8754-42c5-af4a-7900be09703a)

The All-2D MOSFET exhibits excellent electrical performance:

- **Transfer Characteristics (I\(_D\) vs V\(_G\))**: Achieves a high on/off current ratio (>10⁵), demonstrating strong gate control for effective switching.
- **Output Characteristics (I\(_D\) vs V\(_{DS}\))**: Smooth current modulation with increasing V\(_G\) and V\(_{DS}\), indicating good output performance.
- **Mobility**: Field-effect mobility remains constant with increasing gate electric field, showing minimal scattering and high-quality interfaces in the 2D materials stack.

These results highlight the potential of 2D materials like MoS₂, graphene, and h-BN for scalable, high-performance transistor applications.

![image](https://github.com/user-attachments/assets/24936d7c-1d95-4150-adab-639feb54d0b0)

The diagram on the top left shows a non-planar transistor with key components:

- Gate: Controls the flow of current through the channel.
- Channel: Region where current flows between the source (S) and drain (D).
- Body: Underlying region connected to the substrate.
- STI (Shallow Trench Isolation): Insulates neighboring devices.

The biggest challenge is to form a single-crystalline semiconductors on a non-planar surface is difficult using conventional semiconductor fabrication techniques.

![image](https://github.com/user-attachments/assets/09db667f-dd86-4ba5-9357-29bc6124febb)

Single-Layer CMOS (a): This is the traditional CMOS design where NMOS and PMOS transistors are fabricated on a single silicon layer. Each transistor operates in the same planar layer, with devices connected laterally.

Monolithic 3D CMOS (b): In this design, NMOS and PMOS transistors are stacked in two separate layers, enabling higher density. The P-Channel (PMOS) is placed on top of the N-Channel (NMOS), separated by an oxide layer. This approach reduces the footprint and allows better performance due to shorter interconnects.

Single-Layer CMOS Logic (c): Shows logic gates (inverter, 2-input NAND, and 2-input NOR) built using traditional single-layer CMOS. Transistors are laid out horizontally, with interconnections taking more space.

Monolithic 3D CMOS Logic (d): Logic gates are constructed with two transistor layers (Layer 1 and Layer 2), reducing the area required for interconnections. Vertical integration improves performance and reduces delay by shortening signal paths.

![image](https://github.com/user-attachments/assets/a83936b9-267d-4e3f-a1b5-8539b156b712)


**Dual Damascene Cu**, used for the 7nm technology node with a 36nm pitch, combines vias (vertical connections) and lines (horizontal connections) in a single patterning step. It relies on copper (Cu) for interconnections; however, as dimensions shrink, challenges such as gap filling and maintaining reliability become increasingly significant.

**Single Damascene Cu**, used for the 5nm technology node with a 28nm pitch, involves splitting the creation of vias (vertical connections) and lines (horizontal connections) into separate steps. This approach addresses the challenges of smaller dimensions, with a primary focus on reducing resistance (R) in both lines and vias to maintain optimal performance.

**Barrier and via metal optimization**, introduced at the 3nm technology node with a 20-24nm pitch, focuses on reducing the thickness of barrier layers (insulating layers) to minimize resistance while maintaining robust and reliable via connections. This optimization is essential to meet the performance and scaling demands of advanced nodes.

At sub-18nm pitch, **subtractive RIE** and alternative metals like ruthenium (Ru) are introduced to address the reliability and scaling challenges faced by traditional copper interconnects. Subtractive Reactive Ion Etching (RIE) enables more precise patterning of interconnects, while the use of Ru provides improved performance and durability at such advanced dimensions.

For future nodes with pitches below 15nm, **post-Damascene interconnects** featuring tall, barrier-less designs are envisioned. This approach enhances electromigration (EM) reliability, ensuring durable and robust connections despite the continued shrinking of dimensions, thereby addressing key challenges in advanced interconnect scaling.

![image](https://github.com/user-attachments/assets/b0e1ee7f-3987-4ad4-b1ed-6030fcd2b1bf)

The image shows how a selective barrier, typically tantalum nitride (TaN), can improve copper interconnects in semiconductor manufacturing. This barrier reduces resistance, enhances reliability by preventing copper ion migration, and aids in controlling copper thickness. The process involves cleaning the copper surface, depositing TaN using atomic layer deposition (ALD), and removing sacrificial layers. This technique is crucial for advancing semiconductor technology and ensuring reliable, high-performance devices.

![image](https://github.com/user-attachments/assets/b1083105-a723-4f5f-aa37-5f3c5bf1a9be)

**Back-Side Power Delivery Network (BS-PDN)**

In advanced semiconductor manufacturing, efficient power delivery is critical to the performance and reliability of integrated circuits. Traditional Front-Side Power Delivery Networks (FS-PDNs) often suffer from high IR-drop, which can limit device performance and reliability. To address this challenge, Back-Side Power Delivery Networks (BS-PDNs) have emerged as a promising solution.

BS-PDNs involve routing power supply rails on the backside of the chip, enabling shorter and wider power lines. This configuration significantly reduces IR-drop, leading to improved power delivery efficiency. As a result, BS-PDNs offer several advantages:

- Reduced IR-drop: Lower voltage drops across the power network, leading to improved performance and reliability.
- Decreased standard cell area: More efficient power delivery allows for smaller standard cell sizes.
- Improved performance: Lower IR-drop leads to faster switching speeds and reduced power dissipation.

By adopting BS-PDNs, semiconductor manufacturers can develop high-performance and energy-efficient integrated circuits that meet the demands of modern electronics.


**Installing and setting up ORFS**

```
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
```

![Screenshot from 2024-11-20 09-53-58](https://github.com/user-attachments/assets/aebdf533-1723-411a-9b75-5d2f70ae6dd7)



```
./build_openroad.sh --local
```
![Screenshot from 2024-11-20 10-05-55](https://github.com/user-attachments/assets/892f72bb-be3d-4eaa-9b67-35c0dcb25cbf)


Folder Setup

![Screenshot from 2024-11-20 16-09-32](https://github.com/user-attachments/assets/3a1fcc3b-ebbb-44c6-a944-601798445011)

![Screenshot from 2024-11-20 16-37-57](https://github.com/user-attachments/assets/0d7c0c9e-343b-4d07-ac92-580c015fcb5d)

Files Installed

![Screenshot from 2024-11-22 23-07-28](https://github.com/user-attachments/assets/48bfc7e5-961a-4950-9728-de8103b8178d)

![Screenshot from 2024-11-22 23-39-07](https://github.com/user-attachments/assets/d390117a-12d3-4aaa-b64a-be6d9edea984)

![Screenshot from 2024-11-22 23-44-53](https://github.com/user-attachments/assets/471743eb-0c25-4f56-be6b-12946452c1d4)

Verify Installation**

```
source ./env.sh
cd flow
make
```
![Screenshot from 2024-11-23 22-57-05](https://github.com/user-attachments/assets/d58edee4-2a08-4a01-a3ea-48821c714a95)

![Screenshot from 2024-11-23 22-57-19](https://github.com/user-attachments/assets/ce43aecf-eddc-4a81-b816-a89d44bb0c7b)

![Screenshot from 2024-11-23 23-28-26](https://github.com/user-attachments/assets/874f9ef2-194f-4934-8cc0-ed8582a49b37)

```
sudo make gui_final
```
![Screenshot from 2024-11-25 22-52-40](https://github.com/user-attachments/assets/e70e1e97-9975-45c3-add4-47f575822557)


