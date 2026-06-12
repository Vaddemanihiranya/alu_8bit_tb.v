`timescale 1ns/1ps

module alu_8bit_tb;

reg [7:0] A, B;
reg [2:0] Sel;
wire [7:0] Result;

// Instantiate ALU
alu_8bit uut (
    .A(A),
    .B(B),
    .Sel(Sel),
    .Result(Result)
);

initial begin
    A = 8'd10;
    B = 8'd5;

    Sel = 3'b000; #10; // Addition
    Sel = 3'b001; #10; // Subtraction
    Sel = 3'b010; #10; // AND
    Sel = 3'b011; #10; // OR
    Sel = 3'b100; #10; // XOR
    Sel = 3'b101; #10; // NOT
    Sel = 3'b110; #10; // Left Shift
    Sel = 3'b111; #10; // Right Shift

    $finish;
end

initial begin
    $monitor("Time=%0t A=%d B=%d Sel=%b Result=%d",
             $time, A, B, Sel, Result);
end

endmodule
