### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**

1. Define module: Create exp11 with inputs clk, rstn and 4-bit output register out.
2. Declare ports: Specify input clk, rstn; and output reg [3:0] out;.
3. Set clocked process: Write always @(posedge clk) for synchronous operation.
4. Implement reset: If !rstn, assign out <= 4'b0000 (active-low synchronous clear).
5. Increment counter: Else, update out <= out + 1 on each rising clock edge.
6. Verify behavior: Simulate by toggling rstn low→high and confirm count 0→15 then rollover to 0.

**PROGRAM**

/* Program for flipflops and verify its truth table in quartus using Verilog programming. 

Developed by: Eswar S

RegisterNumber: 25017992
*/

```
module exp11 (out,clk,rstn); 
input clk,rstn;
output reg [3:0] out;
always @ (posedge clk)
begin 
	if(!rstn) 
		out<=0; 
	else 
		out <= out+1; 
end 
endmodule
```

**RTL LOGIC UP COUNTER**

<img width="1289" height="555" alt="image" src="https://github.com/user-attachments/assets/ec20fcf6-7de8-4172-b854-7773bcc02c74" />

**TIMING DIAGRAM FOR IP COUNTER**

<img width="1919" height="638" alt="image" src="https://github.com/user-attachments/assets/9faa0987-1384-4b9b-a8cb-ff34aea0ee42" />

**TRUTH TABLE**

<img width="400" height="442" alt="image" src="https://github.com/user-attachments/assets/a261ca50-b491-4889-98c3-aedad595a813" />

**RESULTS**

The synchronous up counter successfully increments its 4‑bit output on each rising clock edge. When reset is applied, the counter clears to zero and resumes counting once reset is released.
