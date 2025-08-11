```verilog
`timescale 1ps/1ps
module tb_seq_1010_non_ovl_moore_dec;
  reg clk,rst_n,x;
  reg exp_z;
  wire z;
  integer err=0;
  
  seq_1010_non_ovl_moore_dec DUT (clk,rst_n,x,z);
  
  always #2 clk = ~clk;
  initial begin
  
    $monitor("time=%0t, clk=%b, rst_n=%b, z=%b | exp_z=%b",$time,clk,rst_n,z,exp_z);
  
  rst_n = 0; x=0; clk = 0; exp_z = 0;
  
  #3; rst_n = 1 ;
  x = 1;
  #4;
  x = 0;
  #4;
  x = 1;
  #4;
  x = 0;
  #2;
  exp_z = 1;
  #3;
  check(z,exp_z);
  #2;
  x = 0;
  #7;
  x = 1;
  #4;
  x = 0;
  #4;
  x = 1;
  #4;
  x = 0;
  #5;
  check(z,exp_z);
  #1;
  x = 1;
  #4;
  x = 0;
  #4;
  x = 1;
  #4;
  x = 0;
  #6;
  check(z,exp_z);
  #1;
  x = 1;
  #4;
  x = 0;
  #4;
  x = 1;
  #2;
  x = 0;
  
  #5;
  
    if(err == 0)begin 
    $display("------------");
    $display("Test Pass");
    $display("------------");
    end else begin 
    $display("------------");
    $display("Test Fail with %d error",err);
    $display("------------");
    end

  $finish;
  end
  
  task check ( input z, input exp_z);
    @(posedge clk);
    if(z !== exp_z) begin
    $display("[CHECK] Error");
    err = err +1;
    end else begin
    $display("[Check] Matching");
    end
  endtask
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars;
  end
endmodule
