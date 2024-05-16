EXP.NO: 04

DATE: 26.03.2024

SIMULATION OF IMPLEMENTATION SEQUENTIAL LOGIC CIRCUITS

AIM: To simulate the following circuits using Vivado 2023.2.

1) SR Flip Flop
2) JK Flip Flop  
3) T- Flip Flop
4) D-Flip Flop
6) Up-down Counter
7) Mod10 Counter
8) Ripple Carry Counter
   
APPARATUS REQUIRED:

VIVADO 2023.2

PROCEDURE: 

STEP:1 Start the Vivado, Select and Name the New project. 

STEP:2 Select the device family, device, package and speed. 

STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. 

STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax. 

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

SR FLIP FLOP:

LOGIC DIAGRAM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/47aa2261-0372-42cc-b4a0-b83eaff73601)

 
VERILOG CODE:

module sr(s,r,clk,rst,q);

input s,r,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else 

begin

case ({s,r})

2'b00: q = q;

2'b01: q = 1'b0;

2'b10: q = 1'b1;

2'b11: q = 1'bx;

endcase

end

end

endmodule

OUTPUT WAVEFORM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/93c1efbe-38e4-4df7-aa9e-581043b07668)

 
JK FLIP FLOP:

LOGIC DIAGRAM:



 
VERILOG CODE:

module jk(j,k,clk,rst,q);

input j,k,clk,rst;

output reg q;

always @ (posedge clk)

begin 
if (rst==1)

q=1'b0;

else 

begin

case ({j,k})

2'b00: q = q;

2'b01: q = 1'b0;

2'b10: q = 1'b1;

2'b11: q = ~q;

endcase

end

end

endmodule

OUTPUT WAVEFORM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/d05b7bb0-7dcc-43f7-8ffc-90059f56d20f)


T-FLIP FLOP:

LOGIC DIAGRAM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/65265778-053b-4a6e-88f7-1a1acb32b49e)

 
VERILOG CODE:

module t(t,clk,rst,q);

input t,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else if (t==0)

q=q;

else

q=~q;

end

endmodule

OUTPUT WAVEFORM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/261e5cb3-5bba-4f0c-9e90-4db6b5d5fbff)

 
D-FLIP FLOP:

LOGIC DIAGRAM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/4a579aae-f45f-448e-8681-c55becae90a1)

 
VERILOG CODE:

module d(d,clk,rst,q);

input d,clk,rst;

output reg q;

always @ (posedge clk)

begin 

if (rst==1)

q=1'b0;

else

q=d;

end

endmodule

OUTPUT WAVEFORM: 


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/7281ea56-3493-4289-b761-d5ccdca38840)


UPDOWN COUNTER:


 ![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/cbd2765b-a5e4-4754-93db-862567570695)
 

VERILOG CODE:

module updowncounter(clk,rst,updown,out);

input clk,rst,updown;

output reg [3:0]out;

always @(posedge clk)

begin

if (rst==1)

out=4'b0000;

else if (updown==1)

out=out+1;

else

out=out-1;

end

endmodule

OUTPUT WAVEFORM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/09ca14fa-b854-4188-815a-b307bce3b961)

 
MOD 10 COUNTER:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/a574586f-b465-4f3e-96bf-97f218371488)

 
VERILOG CODE:

module mod10counter(clk,rst,out);

input clk,rst;

output reg [3:0]out;

always @(posedge clk)

begin

if (rst==1 | out==4'b1001)

out=4'b0000;

else

out=out+1;

end

endmodule

OUTPUT WAVEFORM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/9eaba5fd-900d-48ff-ae64-960b8a4e58a7)

 
RIPPLE CARRY COUNTER:

LOGIC DIAGRAM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/3b3b2219-eb0e-4b07-a5ae-5114741b02b0)


VERILOG CODE :

module ripple_carry_counter(q, clk, reset);

output [3:0] q;

input clk, reset;

T_FF tff0(q[0], clk, reset);

T_FF tff1(q[1], q[0], reset);

T_FF tff2(q[2], q[1], reset);

T_FF tff3(q[3], q[2], reset);

endmodule

module T_FF(q, clk, reset);

output q;

input clk, reset;

wire d;

D_FF dff0(q, d, clk, reset);

not n1(d, q); 

endmodule

module D_FF(q, d, clk, reset);

output q;

input d, clk, reset;

reg q;

always @(posedge reset or negedge clk)

if (reset)

q = 1'b0;

else

q = d;

endmodule

OUTPUT WAVEFORM:


![image](https://github.com/Padmeshwaraan/VLSI-EXPERIMENT-4/assets/160568747/7e323b1c-ab8f-4627-bfd7-e9ede3608946)

 
RESULT:

Thus the simulation of sequential circuits is done and outputs are verified
Successfully.

