# SIMULATION OF LOGIC GATES, ADDERS AND SUBRACTORS USING VIVADO
AIM: 

To simulate and synthesis Logic Gates,Adders and Subtractor using vivado.

APPARATUS REQUIRED: 

Vivado 2023.1

PROCEDURE:

STEP:1 Start the Xilinx navigator, Select and Name the New project.

STEP:2 Select the device family, device, package and speed. 

STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. 

STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. 

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. 

STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. 

STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 

STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 

STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into 
.bit file here. 

STEP:11 Load the Bit file into the SPARTAN 6 FPGA 

STEP:12 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)


Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)


8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)


# LOGIC GATES

VERILOG CODE :
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```

OUTPUT:

![318389975-d761016b-56d4-47ec-9d75-5af644c626a3](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/91bb2913-e79e-40a9-a378-02b849d091c5)

![318390144-8b277866-b2b8-4da3-89d0-954b778a908a](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/145a1a2b-347c-4f74-9e6d-2e9ce4825f8e)




# HALF ADDER
VERILOG CODE :
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry; 
or(sum,a,b);
and(carry,a,b);
endmodule
```

OUTPUT:

![318391026-116d70f4-b698-4d9a-aa13-9c1988b417fe](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/ccab4ebc-4f14-4b3a-bfd9-ae70d45e508d)


![318391177-6642c69c-a68d-42fb-98ee-e2ea36025630](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/24667fab-f2ea-4bfc-8c3b-866a2d2b1b0c)


# FULL ADDER

VERILOG CODE :
```
module fa_ha(a,b,c,sum,cout);
input a,b,c;
output sum,cout;
wire wl, w2, w3, w4, w5;
xor x1(w1,a,b);
xor x2 (sum,w1,c) ;
and al(w2,a,b) ;
and a2(w3,b,c);
and a3(w4,a,c) ;
or o1(w5,w2,w3) ;
or o2(cout,w5,w4) ;
endmodule
```

OUTPUT :
![318387885-a7106ba1-5c5f-4c4d-9d31-66dbad63ce53](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/5e6b929e-1471-493f-8a45-809fd4946dbb)

![318391591-9b5a3e2f-13fc-4a0d-9413-061eeaf3bbef](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/eebe23cd-e265-40c8-9546-dce4a9a0a0a3)



# HALF SUBRACTOR

VERILOG CODE :
```
module halfsubtractor( D,Bo,A,B);
input A,B;
output D,Bo;
wire w1;
xor (D,A,B);
not (w1,B);
and (Bo,B,w1);
endmodule
```

OUTPUT:
![318391833-c2a77dc5-d2be-4a6d-8746-d587cd33f165](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/870faf41-de43-4499-bbad-0866fa568384)

![318391948-f05b66ef-4a79-4520-9751-51004d87db10](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/ac6992e0-0600-4626-a22f-1738a7480d89)



# FULL SUBRACTOR

VERILOG CODE :
```
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule
```

OUTPUT :

![318393204-0943900d-f719-4d70-8365-347baf71d8a8](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/640d0b33-c592-4419-96db-d5468f1b0e0b)

![318393379-72507552-3a34-4f9b-9e30-5bdf9b0c92ca](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/27b2f379-936f-48c1-9b12-e9a6a89a9d93)




# RIPPLECARRYADDER 4_Bit

VERILOG CODE :
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```

OUTPUT :

![318393921-17dbf7a9-a78c-4fc7-89c3-fe940920a391](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/50f5981c-7e0d-494c-8b0d-0f3d45d4f325)

![318394178-a404cdfd-d668-4454-96c0-362af02cd11a](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/7d501838-0f45-42db-b724-1ee5fe67afb9)




# RIPPLECARRYADDER 8_Bit

VERILOG CODE :
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```

OUTPUT :

![318394309-40d226f6-3670-4f58-9a4d-6ecafbe1f280](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/1ccc4aa2-f713-482f-beec-58b68ec04349)

![318394413-19f56c9b-3449-40f9-b5a6-22678a165522](https://github.com/santhoshoff/VLSI-LAB-EXP-1/assets/143347356/ef96f992-69da-4941-9196-fbdc32e38ec2)

RESULT:
Thus the simulation of Logic Gates, Adders and Subtractor is completed using Vivado.
