---
aliases:
  - 串行乘法器
tags:
  - multiplier
  - digital
  - arthmetic_modules
---
![[Bit-Serial Multiplier.png#pic_center|Bit-Serial Multiplier]]
![[Pasted image 20241029041648.png#pic_center|]]
$$Q=M\times A$$
- 对于$M$位与$N$位数相乘，最终需要$N$个周期完成计算。上图的例子需要4个周期
- 与门用来产生[[Partial Products|部分积]]，在实现中需要将$A$的部分填充至总线位宽（我写了一个Verilog代码来验证它）：
```verilog
and_out = M & {6{Q[0]}};
```

附：Verilog代码
```verilog
module multiplier(
input clk,
input n_rst,
input [5:0]M,
input [3:0]N,
output reg [9:0]Q
);

wire [5:0] and_out;
assign and_out = M & {6{Q[0]}};

wire [6:0] adder_out;
assign adder_out = Q[9:4] + and_out;

always@(posedge clk) begin
	if(n_rst==0) begin
		Q <= {6'd0, N};
	end else begin
		Q <= {adder_out, Q[3:1]};
	end
end
endmodule
```