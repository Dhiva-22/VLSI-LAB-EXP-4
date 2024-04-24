# VLSI-LAB-EXP-4
## SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

## APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA
  
## PROCEDURE:
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


## SR FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

### Verilog Code:

```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```

### Output:
![324836921-4baabba2-7e30-4587-a960-75a588677d4c](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/3cf99866-6869-4298-8769-90ecd4ceaf66)




## JK FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

### Verilog Code:

```
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
```

### Output:
![324837060-77f7512b-8bd4-4491-9ecb-fbbdd1512946](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/fb8b7161-1e1e-4bfa-9f00-dfbe3b9bf8fd)




## T FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

### Verilog Code:

```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```

### Output:
![324837149-97dda3a9-e2f5-4cfe-81fa-1e3b444a4a1d](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/b1c8c701-cc03-4938-bf28-6e810f09bbda)




## D FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

### Verilog Code:

```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```

### Output:
![324837294-1d8b7801-c95e-467e-aa6d-a73963c7858e](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/0b35f05b-896a-45eb-b223-b3f9c714f9cb)




## COUNTER:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

## Updown Counter:

### Logic Diagram:
![324838214-85acb718-12c3-4a72-b39d-86af8fc6d98d](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/0749c8f8-e5e1-4516-9622-9c0984cd1af8)




### Verilog Code:

```
module udc(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```

### Output:
![324837447-a05afbf3-5d51-440e-8751-8a8db642548a](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/1341081e-2d76-467b-b285-61e3f50d428d)



## Mod-10 Counter:

### Logic Diagram:
![324837615-7f34c387-c4a2-42e9-92d3-8ad10a7fe658](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/05ab0deb-ff46-40c2-9ab6-5cda303ee447)



### Verilog Code:

```
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```

### Output:
![324837714-3d51965f-70ad-403f-a908-3978b841d049](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/de22c89b-c0e2-4f26-a923-ddc3255db37a)




## Ripple Carry Counter:

### Logic Diagram:

![324838836-86953473-e21f-4185-ad89-fe8965cefa24](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/80ac6c2b-d460-4e35-9ebd-4c43d3633f2a)


![324838890-d7c60d2a-64f8-47e8-b144-e1b81aee87e9](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/c3b0d38f-b0b1-45ec-8b01-441ff73380e6)







### Verilog Code:

```
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
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module rcc(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf2(q[1],q[0],rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
```

### Output:
![324838104-fa96f225-df0b-4637-9912-6e6444ee95f7](https://github.com/Dhiva-22/VLSI-LAB-EXP-4/assets/161815121/acfe927d-9ad8-41a8-8dd4-1f94b40c4a43)




## RESULT:
 Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Xilinx ISE.


