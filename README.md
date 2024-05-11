# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

APPARATUS REQUIRED:

Xilinx 14.7

PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

**LOGIC DIAGRAM**

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

CODE
```
module srff(s,r,clk,reset,q);
input s,r,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({s,r})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = 1'bx;
 default:q = ~q;
endcase
end 
end
endmodule
```
OUTPUT
![SR FLIPFLOP](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/c0a8fa97-3dbf-4caa-8506-5b2f7b804ca9)

JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

CODE
```
module jk_ff(j,k,clk,reset,q);
input j,k,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({j,k})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = ~q;
 default:q =1'b0;
endcase
end 
end
endmodule
```
OUTPUT
![JK FLIPFLOP](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/42866cbf-0aca-47f3-b371-ce77043f5d98)

T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

CODE
```
module tff(clk,rst,j,q);
input clk,rst,j;
output reg q;
always@(posedge clk)
begin
case(t)
1'b0:q=q;
1'b1:q=~q;
default=q=1'b0;
endcase
end
endmodule
```
OUTPUT
![T FLIPFLOP](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/9c962287-8991-4d7c-86c6-05a7cbbd31fa)

D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

CODE
```
module dff(clk,rst,d,q);
input clk,rst,d;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=1'b0;
else
q=d;
end
endmodule
```
OUTPUT
![D FLIPFLOP](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/99497774-5a3e-4993-9ab1-257d510fcea4)

COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

UPDOWNCOUNTER

![UPDOWNCONTER](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/3f8da406-66bb-42b2-9d13-30b3e2b754bb)

CODE
```
module updown(clk,rst,up_down,count);
input clk,rst,up_down;
output reg[3:0]count;
always@(posedge clk)
begin
if(rst==1)
count <= 4'b0000;
else if (up_down == 1'b1)
count <= count + 1'b1;
else
count <= count-1'b1;
end
endmodule
```

OUTPUT

![UPDOWNCOUNTER](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/f75994ba-0721-4770-bee3-71c9e6cc8aa8)

MOD10COUNTER

![MOD10COUNTER](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/f58ec6b9-2ba9-4212-bfdf-5c295b73cce0)

CODE
```
module mod(clk,rst,count);
input clk,rst;
output reg[3:0]count;
always @(posedge clk)
begin
if(rst==1 | count==4'b1001)
count <= 4'b0000;
else
count <= count +1;
end
endmodule
```

OUTPUT

![MOD10COUNTER](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/5511396b-718d-4a4d-a09f-8fea088c7315)

RIPPLECARRYADDER

![RCA](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/fd5c4357-d2ef-44af-b0e0-8c695692e356)
![RCA](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/93e54f28-1a13-499d-8116-8551df016f1b)

CODE
```
module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tff1(q[0],clk,rst);
tff tff2(q[1],q[0],rst);
tff tff3(q[2],q[1],rst);
tff tff4(q[3],q[2],rst);
endmodule
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always@(posedge clk or posedge rst)
begin
if(rst)
q=1'b10;
else
q=d;
end
endmodule
```
OUTPUT
![RCA](https://github.com/Thirugnanaselvan/VLSI-LAB-EXP-4/assets/160720772/943d710e-f201-48b4-8e7f-9b0ea05991c7)

RESULT
Thus,the simulation and synthesis of SR,JK,T,D flipflops,counters by using vivado has been successfully excecuted and verified.
