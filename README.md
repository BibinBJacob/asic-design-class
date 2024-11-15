

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
