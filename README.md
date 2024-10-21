

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























