<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html><head><title>Additions to package standard</title>
<!-- Changed by: , 26-Aug-2009 -->
  <meta name="description" content="Additions to the VHDL std.standard package">
  <meta name="author" content="dbishop@vhdl.org">
<META NAME=keywords CONTENT="standard_addtions, VHDL, VHDL-2008">
<META NAME=identifier-url CONTENT="http://vhdl.org/fphdl/std_additions.html">
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
 <a href="standard_additions_c.vhdl">standard_additions</a> -- Additions to the package "std.standard"
</p>
<p>
   Use model:<br>
   <b>use ieee_proposed.standard_additions.all;</b><br>
   Dependancies: None.
</p><p>
   Notes:  The functions "rising_edge" and "falling_edge" are defined in
   this package.  If you use "numeric_bit" they are ALSO defined in that
   package, causing a conflict.  The VHDL-200X-FT version of numeric_bit
   has these functions commented out, as well as the "sll", "srl", "ror"
   and "rol" functions which are implicit.
</p>
 <ul> New types defined in this package:
   <li>   REAL_VECTOR  - A vector of type real
   <li>   TIME_VECTOR  - A vector of type time
   <li>   INTEGER_VECTOR - A vector of type integer
   <li>   BOOLEAN_VECTOR - a vector of type boolean
</ul>
<ul>
   New constants defined in this package:
   <li>   SIM_RESOLUTION : TIME - returns the simulator's resolution (1 ns default)
</ul>
<ul>New funcitons defined in this package:
  <li> "maximum" and "minimum" are defined for all default datatypes
   <li> _reduce functions (and_reduce, nand_reduce, or_reduce ...) are defined
      These functions reduce a bit_vector to a single bit.<br>Example:<br>
      <b>or_reduce ("0101") = '1'</b>
<br>In VHDL-2008 syntax these will be "or".
   <li> "vector" and "bit" operations are defined.  These will perform a
      boolean operation of a vector.<br>Example:<br>
      <b>"1" xor "1010" = "0101";</b>
  <li> /??/ function is defined for "bit" ("??" operator is release)
      <b>if (/??/('1')) then -- will return a "true".</b>
  <li> rising_edge and falling_edge functions are defined (see Notes).
  <li> to_string function - Converts any of the base types into a string.<br>
      Example: <br>
      <b>assert (bv = "101") report "result was " & to_string(bv) severity note;</b>
   <li> to_hstring and to_ostring function (bit_vector to hex or octal string)
</ul>

Please send feedback to <em>David W. Bishop
<a href="mailto:dbishop@vhdl.org">dbishop@vhdl.org</a></em>. &nbsp

</font>
</body>
</html>