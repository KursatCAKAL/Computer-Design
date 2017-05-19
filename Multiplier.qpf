module ALU(Carpan,Carpilan,Result,AluOp,Ainvert,Binvert,Zero);
input [4:0] Carpan,Carpilan;
output reg [7:0] Result;//Normalde Result register deđil.
input [1:0] AluOp;
input Ainvert,Binvert;
output Zero;

always
   case ({Ainvert,Binvert,AluOp})
	 	4'b0010: Result=A+B;
   endcase
assign Zero=(Result==0);
endmodule


module Product(Carpim,Carpan,Carpilan)
input [7:0] Carpim;
input [3:0] Carpan,Carpilan;

always @(posedge clk)
if(Carpan[0]==0)
{
assign Carpim={{1'b0},{Carpim[7:1]}};//sađa kaydýrdýk
assign Carpan={{1'b0},{Carpan[3:1]}};
}

if(Carpan[0]==1)
{
assign Carpim[7:4]=Carpim[7:4]+Carpilan;
assign Carpim={{1'b0},{Carpim[7:1]}};//sađa kaydýrdýk
assign Carpan={{1'b0},{Carpan[3:1]}};
}

endmodule


module topModule(sayiCarpan,sayiCarpilan,Basla,Hazir,CLK)

input [3:0] Carpan,Carpilan;
input Basla,CLK;
output Hazir;
wire [7:0] CarpimKablo;
wire zero;

ALU instAlu(.A(Carpan),.B(Carpilan),.Result(CarpimKablo),2'b10,1'b0,1'b0,zero);
Product instProduct(.Carpim(CarpimKablo),.Carpan(Carpan),.Carpilan(Carpilan));

endmodule
