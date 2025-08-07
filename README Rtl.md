```verilog
module d_ff_sync_rst_n (input wire d, clk , rst_n,
                        output reg q);
  
  always @ (posedge clk) begin
  
    if( rst_n ==0)
      q <= 0;
    else
      q <= d;
  end
endmodule
