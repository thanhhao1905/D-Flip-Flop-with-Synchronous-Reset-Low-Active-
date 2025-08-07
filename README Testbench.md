```verilog
`timescale 1ns/1ps
module tb_d_ff_sync_rst_n;
  reg d , clk , rst_n;
  wire q;
  
  d_ff_sync_rst_n DUT (d ,clk ,rst_n ,q);
  
  always #2 clk = ~clk;
  
  initial begin
    clk = 0;
    rst_n = 0;
    d = 0;
    
    #1 rst_n = 1;
    #5 d = 1;
    #5 d = 0;
    #5 d = 1;
    #5;
    
    #1 rst_n = 0;
    #5 d = 0;
    #5 d = 1;
    #5;
    
    $finish;
  end
  
  initial begin
    $dumpfile("dumpfile.vcd");
    $dumpvars;
  end
endmodule
