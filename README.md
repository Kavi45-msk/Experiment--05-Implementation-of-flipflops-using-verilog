# NAME: KAVI M S
# REFERENCE NUMBER: 23013458

# Experiment--05-Implementation-of-flipflops-using-verilog
### AIM: To implement all the flipflops using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
## PROCEDURE
1.Using nand gates and wires construct sr flip flop.

2.Repeat same steps to construct JK,D,T flipflops.

3.Find Rtl logic and timing diagram for all flipflops.

4.end the program
## SR Flip-Flop
SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

![image](https://user-images.githubusercontent.com/36288975/167910294-bb550548-b1dc-4cba-9044-31d9037d476b.png)

 
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable.
The following table shows the state table of SR flip-flop.


![image](https://user-images.githubusercontent.com/36288975/167910648-ced88e69-869c-42e2-9718-a285a3902446.png)


Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop.
Present Inputs	Present State	Next State


![image](https://user-images.githubusercontent.com/36288975/167908180-5fc9d589-1cb5-41f5-b2c8-927e04f5f387.png)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

![image](https://user-images.githubusercontent.com/36288975/167908214-25b30a54-db20-4bcb-9385-5f93a1982a09.png)

 
The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is
Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)

# PROGRAM
```
module sr(S,R,clk,Q,Qbar);
input S,R,clk;
output reg Q;
output reg Qbar;
initial Q=0;
initial Qbar=1;
always @(posedge clk)
begin
Q=S|((~R)&Q);
Qbar=R|((~S)&(Qbar));
end
endmodule
```

# RTL LOGIC FOR SR-FLIPFLOP
![292276317-f2cd191f-27d5-4572-8c50-3409ba4eaeab](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/ce5a7829-502e-4b27-b0e9-abdda7a25b0a)

# TRUTH TABLE FOR SR-FLIPFLOP
![292276265-a5369caf-d15f-4cf1-99dc-9a28c3f699fa](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/e38c80df-9eaf-45cc-a7bc-1dc4b9161468)

# TIMING DIAGRAM FOR SR-FLIPFLOP
![292276240-efd8c0f6-9cbb-4d01-9046-10d08a2da699](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/6ae04ff9-eb5d-4025-9294-2c2b8b34460d)

### D Flip-Flop
D flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, D latch operates with enable signal. That means, the output of D flip-flop is insensitive to the changes in the input, D except for active transition of the clock signal. The circuit diagram of D flip-flop is shown in the following figure.
 
This circuit has single input D and two outputs Qtt & Qtt’. The operation of D flip-flop is similar to D Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable.
The following table shows the state table of D flip-flop.
![image](https://user-images.githubusercontent.com/36288975/167908342-e03f0cbb-5958-43bb-b74a-5e3ec2341675.png)

![image](https://user-images.githubusercontent.com/36288975/167910325-aeef0739-0a54-40e2-bebd-6f5fa0cad10e.png)



Therefore, D flip-flop always Hold the information, which is available on data input, D of earlier positive transition of clock signal. From the above state table, we can directly write the next state equation as
Qt+1t+1 = D



![image](https://user-images.githubusercontent.com/36288975/167908850-d39d07ba-7f9d-490a-b9f2-274e189fd047.png)

Next state of D flip-flop is always equal to data input, D for every positive transition of the clock signal. Hence, D flip-flops can be used in registers, shift registers and some of the counters.

# PROGRAM
```
module d(d,clk,q,qbar);
input d,clk;
output q,qbar;
reg q,qbar;
always @(posedge clk)
begin
q=d;
qbar=~q;
end
endmodul
```

# RTL LOGIC FOR D-FLIPFLOP
![292276688-d1f28eed-98da-49ce-a52a-ca1e128db7ae](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/7d8c2735-9f97-4117-8555-dc664f6a0066)

# TRUTH TABLE FOR D-FLIPFLOP
![292276704-d47c913d-b897-42ca-a104-ccdb45905357](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/11eb80fe-1f9c-4357-b1c6-294a7dd20480)

# TIMING DIAGRAM FOR D-FLIPFLOP
![292276722-b38dfab4-c998-4a73-893f-bea95b5dcf6b](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/e9863b55-f811-4850-8045-d31129cbf40c)

### JK Flip-Flop
JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.
![image](https://user-images.githubusercontent.com/36288975/167910378-d2d984a7-2815-4d17-8c41-ee4bdf59ec24.png) 

 
This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs.
The following table shows the state table of JK flip-flop.


![image](https://user-images.githubusercontent.com/36288975/167908575-59c35afb-50d3-46a2-888c-47478a3179d5.png)

Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop.
Present Inputs	Present State	Next State

![image](https://user-images.githubusercontent.com/36288975/167908664-c854ffe9-0bd3-44c2-bfa6-e53928181c69.png)


By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
 
 
 ![image](https://user-images.githubusercontent.com/36288975/167908688-fa93c3e9-8323-4864-947d-c11d163d5a90.png)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is
Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

# PROGRAM
```
module jk(J,K,clk,Q,Qbar);
input J,K,clk;
output reg Q;
output reg Qbar;
initial Q=0;
initial Qbar=1;
always @(posedge clk)
begin
Q=(J&(~Q))|((~K)&Q);
Qbar=((~J)&(Qbar))|K&(~Qbar);
end
endmodule
```

# RTL LOGIC FOR JK-FLIPFLOP
![292277058-7b23c3f0-24fd-4f41-bd8f-687fc538d5f3](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/ac2b29a9-44ad-4328-b2b1-3fd26e0e16d6)

# TRUTH TABLE FOR JK-FLIPFLOP
![292277015-1d87535b-8e5c-4d51-9400-b058bc666ed7](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/b3dd7c30-a15d-4a98-b1d3-50dfe7e3a377)

# TIMING DIAGRAM FOR JK-FLIPFLOP
![292276805-121879af-c45c-431a-803f-3be9b232f3e7](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/4325b01a-7704-4ccc-9030-7899d9518380)

### T Flip-Flop
T flip-flop is the simplified version of JK flip-flop. It is obtained by connecting the same input ‘T’ to both inputs of JK flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of T flip-flop is shown in the following figure.

![image](https://user-images.githubusercontent.com/36288975/167911534-5f3c445d-bc68-46e2-9a9c-7efce5febc60.png)



This circuit has single input T and two outputs Qtt & Qtt’. The operation of T flip-flop is same as that of JK flip-flop. Here, we considered the inputs of JK flip-flop as J = T and K = T in order to utilize the modified JK flip-flop for 2 combinations of inputs. So, we eliminated the other two combinations of J & K, for which those two values are complement to each other in T flip-flop.
The following table shows the state table of T flip-flop.



Here, Qtt & Qt+1t+1 are present state & next state respectively. So, T flip-flop can be used for one of these two functions such as Hold, & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of T flip-flop.
Inputs	Present State	Next State


![image](https://user-images.githubusercontent.com/36288975/167909015-53aa9450-3f28-4202-887a-79d88228f8a0.png)

From the above characteristic table, we can directly write the next state equation as
Q(t+1)=T′Q(t)+TQ(t)′
⇒Q(t+1)=T⊕Q(t)

# PROGRAM 
```
module t(clk,T,q,qbar);
input clk,T;
output q,qbar;
reg q,qbar;
always @(posedge clk)
begin
q=(T&~q)|(~T&q);
qbar=~q;
end
endmodule
```

# RTL LOGIC FOR T-FLIPFLOP
![292277452-27812f8e-26ba-4b08-a493-18df8e0f0ecc](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/84e87d04-32da-408f-a5eb-1a5b3cd068d2)

# TRUTH TABLE FOR T-FLIPFLOP
![292277472-9dfaefb6-c378-412b-90f3-ddca4da3aeba](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/0fc64a53-3242-44cc-b95a-6f512c2ca057)

# TIMING DIGRAM FOR T-FLIPFLOP
![292277490-ca6c5a0a-d2da-4ad7-9956-29580af0a355](https://github.com/Kavi45-msk/Experiment--05-Implementation-of-flipflops-using-verilog/assets/147457752/b1c6145d-144d-48fb-849a-2ac485393e24)

# RESULTS 
Thus implementation of SR,JK,D and T flipflops using nand gates are done sucessfully

