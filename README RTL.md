```verilog
module seq_1010_non_ovl_moore_dec (input wire clk, rst_n, x,
                                   output reg z);
 
  parameter A = 4'b0000;
  parameter B = 4'b0001;
  parameter C = 4'b0010;
  parameter D = 4'b0101;
  parameter E = 4'b1010;
  
  reg [3:0] state, next_state;
  
  always @ (posedge clk or negedge rst_n) begin
    if(rst_n == 0)
      state <= A;
    else
      state <= next_state;
  end
  
  always @(state or x) begin
    case(state)
      A: if (x==0) begin next_state = A;
        end else begin next_state = B;
        end
      B: if (x==0) begin next_state = C;
        end else begin next_state = B;
        end
      C: if (x==0) begin next_state = A;
        end else begin next_state = D;
        end
      D: if (x==0) begin next_state = E;
        end else begin next_state = B;
        end
      E: if (x==0) begin next_state = A;
        end else begin next_state = B;    // non_overlapping
          // else begin next_state = D;   ovelapping
        end
      default: next_state = A;
    endcase
  end
  
  always@(state)begin
    case(state)
      A: z = 0;
      B: z = 0;
      C: z = 0;
      D: z = 0;
      E: z = 1;
      default: z = 0;
    endcase
  end
  
endmodule
