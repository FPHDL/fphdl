<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html><head><title>Fixed and Floating point support page</title>
<!-- Changed by: , 27-Aug-2009 -->
  <meta name="description" content="Support for the fixed and floating point VHDL and Verilog packages">
  <meta name="author" content="dbishop@vhdl.org">
<META NAME=keywords CONTENT="fixed point, floating point, VHDL, Verilog">
<META NAME=identifier-url
CONTENT="">
<META NAME=distribution CONTENT=Global>
<META NAME=rating CONTENT=General>
<META NAME=copyright CONTENT=>
<META NAME=revisit-after CONTENT=1 days>
<META NAME=resource-type CONTENT=document>
<META NAME=reply-to CONTENT="dbishop@vhdl.org">
<META NAME=robots CONTENT=all>
<META NAME=language CONTENT=en>
<META HTTP-EQUIV=CONTENT-type CONTENT=text/html; charset=iso-8859-1>
</head>
<body bgcolor="#FFFFFF" text="#000000" link="#0000FF" vlink="#007F00">
<p align="right"><FONT face=Arial color=#cecece size=6 Helvetica, sans-serif>
<b><i>Fixed and Floating point support page</i></b></font></p>

<FONT size=2 Helvetica, sans-serif>

<p>
The floating point packages were designed to be 100%
<a href="http://grouper.ieee.org/groups/754/"
target="_top">IEEE 754</a> compatible.  &nbsp
For synthesis, this just isn't practical. &nbsp
I recommend that you that you go into the top of "float_pkg" and change the constants as follows:<pre>
    constant float_exponent_width : NATURAL    := 8;
    constant float_fraction_width : NATURAL    := 15;  -- 16 bits of precision
    constant float_round_style    : round_type := round_zero; -- disable rounding
    constant float_denormalize    : BOOLEAN    := false; -- no denormal numbers
    constant float_check_error    : BOOLEAN    := false; -- NO NAN and overflow checks
    constant float_guard_bits     : NATURAL    := 0; -- no guard bits
In your source code, you should use this type:
  begin
    signal float1 : float (float_exponent_width downto -float_fraction_width);
</pre>


</p>
<p>
If you are an EDA vendor, and would like to test your tool against these packages, please download the "<a href="modeltech.zip" target="_top">modeltech.zip</a>"
(which has the fewest changes in it) and try it aginst your syntheis/simulation
tool.  If you have any issues please drop me an e-mail.
</p>
<p>
The NEXT step is a Verilog package.  Interested?
</p>
<p>
Questions or comments?  Please e-mail me.
dbishop"at"vhdl.org
</font>
</body>
</html>
 
