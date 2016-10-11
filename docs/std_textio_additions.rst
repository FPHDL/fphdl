<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html><head><title>Additions to package textio</title>
<!-- Changed by: , 26-Aug-2009 -->
  <meta name="description" content="Support and compatibility packages for the VHDL-2008 standard">
  <meta name="author" content="dbishop@vhdl.org">
<META NAME=keywords CONTENT="standard_addtions, VHDL, VHDL-2008">
<META NAME=identifier-url CONTENT="http://vhdl.org/fphdl/std_textio_additions.html">
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
 <a href="standard_textio_additions_c.vhdl">standard_textio_additions.vhdl</a> -- Additions to the package "std.textio"
</p>
<p>
   Use model:<br>
   <b>use ieee_proposed.standard_textio_additions.all;</b>
</p><p>
   Dependencies:<br>
   <b>use std.textio;<br>use ieee_proposed.standard_additions;</b>
</p>
<ul>
   <li> tee - Echos the string to BOTH the file and the screen
   <li> SREAD and SWRITE - String read and write routines<br>(so you no longer
      need to do write (L, string'("ABCEDFG"));
   <li> HREAD and HWRITE (Hex read and write) for bit_vector
   <li> OREAD and OWRITE (octal read and write) for bit_vector
   <li> BREAD and BWRITE (binary read and write, same as "READ" and "WRITE" for
      bit_vector
   <li> justify - Justify a string left or right with a width.<br>Example:<br>
      <b>justify ("ABCD", left, 6);</b> will result in "ABCD&nbsp&nbsp"
</ul>
Please send feedback to <em>David W. Bishop
<a href="mailto:dbishop@vhdl.org">dbishop@vhdl.org</a></em>. &nbsp

</font>
</body>
</html>