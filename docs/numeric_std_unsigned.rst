<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html><head><title>Package numeric_std_unsigned</title>
<!-- Changed by: , 26-Aug-2009 -->
  <meta name="description" content="VHDL package numeric_std_unsigned">
  <meta name="author" content="dbishop@vhdl.org">
<META NAME=keywords CONTENT="standard_addtions, VHDL, VHDL-2008">
<META NAME=identifier-url CONTENT="http://vhdl.org/fphdl/numeric_std_unsigned.html">
<META NAME=distribution CONTENT=Global>
<META NAME=rating CONTENT=General>
<META NAME=copyright CONTENT=>
<META NAME=resource-type CONTENT=document>
<META NAME=reply-to CONTENT="dbishop@vhdl.org">
<META NAME=robots CONTENT=all>
<META NAME=language CONTENT=en>
<META HTTP-EQUIV=CONTENT-type CONTENT=text/html; charset=iso-8859-1>
</head>
<body bgcolor="#FFFFFF" text="#000000" link="#0000FF" vlink="#007F00">
<p>
<p>
 <a href="numeric_std_unsigned_c.vhdl">numeric_std_unsigned.vhdl</a> This package
is a "standardized" verion of "std_logic_unsigned" which appears in many
vendor tools.
</p>
<p>
   Use model:<br>
  <b>use ieee.std_logic_1164.all;<br>
   use ieee.numeric_std.all;<br>
   use ieee_proposed.numeric_std_additions.all;</b>
   use ieee_proposed.numeric_std_unsigned.all;</b>
</p>
<p>VHDL-2008 use model:<br>
<b>use ieee.numeric_std_unsigned.all;</b>
</p>
<p>
   Dependencies:  ieee.std_logic_1164, ieee.numeric_std
</p>
<p>
This package treats "std_logic_vector" and "std_ulogic_vector" just like the
"unsigned" type in ieee.numeric_std.  It has all of the funcitionality of the
old "std_logic_unsigned" package with the ability to use "std_ulogic_vector".
</p>
Please send feedback to <em>David W. Bishop
<a href="mailto:dbishop@vhdl.org">dbishop@vhdl.org</a></em>. &nbsp

</font>
</body>
</html>