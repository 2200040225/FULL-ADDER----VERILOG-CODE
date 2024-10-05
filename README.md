Design code :

//gate level modelling

module fulladder(a,b,cin,s,c);
input a,b,cin;
output s,c;
wire w1,w2,w3,w4;
xor(s,w1,a);
and(w2,a,b);
and(w3,b,cin);      
and(w4,cin,a);
or(c,w1,w2,w3);
endmodule

//data flow modelling

module fulladder_tb(a,b,cin,s,c);
input a,b,cin;
output s,c;
assign s=a^(b^cin);
assign c=(a&b)|(b&cin)|(cin&a);
endmodule


Test bench :

module fulladder_tb();
reg a,b,cin;
wire s,c;
fulladder uut(a,b,cin,s,c);
a=0;b=0;cin=0;
#10
a=1;b=1;cin=0;
#10
a=0;b=1;cin=1;
#10
a=1;b=1;cin=1;
#10
a=0;b=1;cin=0;
#10
end
$finish();
endmodule
