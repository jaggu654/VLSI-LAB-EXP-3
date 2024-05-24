**SIMULATION AND IMPLEMENTATION OF MULTIPLIER**

**AIM:**

 To simulate and synthesis multiplier using Vivado 2023.2.

**APPARATUS REQUIRED:**

Vivado 2023.2
  
**PROCEDURE:**

STEP:1 Start the Vivado, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.


**2 BIT MULTIPLIER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

**VERILOG CODE:**

```
module HalfAdder(a,b,sum,carry);
input a,b;
output sum,carry;
xor (sum,a,b);
and (carry,a,b);
endmodule

module twomul(a,b,y);
input [1:0]a,b;
output [3:0]y;
wire w1,w2,w3,w4;
and a1(y[0],a[0],b[0]);
and a2(w1,a[1],b[0]);
and a3(w2,a[0],b[1]);
and a4(w3,a[1],b[1]);
HalfAdder h0(w1,w2,y[1],w4);
HalfAdder h1(w3,w4,y[2],y[3]);
endmodule
```

**OUTPUT:**

![332094838-06c44dc3-62cf-4fb1-adc8-fe52ff8c89d1](https://github.com/jaggu654/VLSI-LAB-EXP-3/assets/167850134/9ee1bba9-a699-4718-91a1-5dfed4f0ea92)

**4 BIT MULTIPLIER:**

**LOGIC DIAGRAM:**

![301736800-d95215dd-8cf1-4e08-93cc-96adfdd7fbdc](https://github.com/jaggu654/VLSI-LAB-EXP-3/assets/167850134/d3c17a3a-2547-44b7-8ce2-73dcef8c4c06)


**VERILOG CODE:**

```
module  ha (a,b,s,c);
input a,b;
output s,c;
xor g1(s,a,b);
and g2(c,a,b);
endmodule
module fa(a,b,c,sum,carry);
input a,b,c;
output sum ,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
xor g2(sum,w1,c);
and g3(w2,w1,c); 
and g4(w3,a,b);
or g5(carry,w2,w3);
endmodule
module fourmul(x,y,z);
input [3:0]x,y;
output [7:0]z;
wire [17:1]w;
and(z[0],x[0],y[0]);
ha hal (x[1]&y[0],x[0]&y[1], z[1],w[1]);
fa fal (x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);
fa fa2 (x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);
ha ha2 (x[3]&y[1],w[3],w[7],w[4]);
ha ha3 (w[5], x[0]&y [2],z[2],w[8]); 
fa fa3 (w[6],x[1]&y[2],w[8], w[12], w[9]);
fa fa4 (w[7],x[2]&y[2],w[9],w[13],w[10]);
fa fa5 (w[4],x[3]&y[2],w[10],w[14], w[11]);
ha ha4 (w[12], x[0]&y[3], z[3], w[15]);
fa fa6 (w[13],x[1]&y[3],w[15],z[4],w[16]);
fa fa7 (w[14],x[2]&y[3],w[16], z[5],w[17]);
fa fa8 (w[11],x[3]&y[3],w[17],z[6],z[7]);

endmodule
```

**OUTPUT:**

![332094768-a8a93391-e9c1-4c99-a808-36103d09788e](https://github.com/jaggu654/VLSI-LAB-EXP-3/assets/167850134/008c5c81-1b7c-49e9-8db7-5a642a851d54)

**RESULT:**

Hence the 2 bit multiplier and 4 bit multiplier are simulated and synthesised using Vivado 2023.2



