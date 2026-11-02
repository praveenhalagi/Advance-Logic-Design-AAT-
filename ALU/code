module alu (
    input  [3:0] A, B,
    input  [2:0] sel,
    output reg [3:0] result,
    output zero
);
always @(*) begin
    case (sel)
        3'b000: result = A + B;
        3'b001: result = A - B;
        3'b010: result = A & B;
        3'b011: result = A | B;
        3'b100: result = A ^ B;
        default: result = 4'b0000;
    endcase
end
assign zero = (result == 4'b0000);
endmodule

module alu_tb;
reg [3:0] A, B;
reg [2:0] sel;
wire [3:0] result;
wire zero;
alu dut(.A(A), .B(B), .sel(sel), .result(result), .zero(zero));
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(0, alu_tb);
end
initial begin
    A=4'd5; B=4'd3; sel=3'b000; #10;
    sel=3'b001; #10;
    sel=3'b010; #10;
    sel=3'b011; #10;
    sel=3'b100; #10;
    A=4'd4; B=4'd4; sel=3'b001; #10;
    $finish;
end
initial begin
    $monitor("t=%0t A=%d B=%d sel=%b result=%d zero=%b",
             $time,A,B,sel,result,zero);
end
endmodule
