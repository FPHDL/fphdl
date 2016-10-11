<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html><head><title>Additions to package ieee.std_logic_1164</title>
<!-- Changed by: , 26-Aug-2009 -->
  <meta name="description" content="Additions to the VHDL ieee.std_logic_1164 package">
  <meta name="author" content="dbishop@vhdl.org">
<META NAME=keywords CONTENT="std_logic_1164, VHDL, VHDL-2008">
<META NAME=identifier-url CONTENT="http://vhdl.org/fphdl/std_logic_1164_additions.html">
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
 <a href="std_logic_1164_additions.vhdl">std_logic_1164_additions.vhdl</a> -- Additions to the package "ieee.std_logic_1164".  This package now includes what used to be in "std_logic_textio", so it must be commented out.  Otherwise it will
conflict with the new functions (which are much more forgiving).
</p>
<p>
   Usage model:<br>
   <b>use ieee.std_logic_1164.all;<br>
   -- use ieee.std_logic_textio.all; -- Comment out, included in "_additions".<br>
   use ieee_proposed.std_logic_1164_additions.all;</b>
<p>
   Dependencies: ieee.std_logic_1164;
</p>
<p>
   Note:  The contents of the "std_logic_textio" package have now been
   included in the "std_logic_1164" package, and an EMPTY "std_logic_textio"
   package is provided in the new release.
</p>
<ul>New funcitons defined in this package:
   <li> Short had aliases:<ul>
      <li> to_bv - calls "to_BitVector"
      <li>to_slv - calls "to_StdLogicVector"
      <li>to_sulv - calls "to_stdULogicVector"
</ul>
   <li> Long hand aliases:<ul>
     <li> to_bit_vector - calls "to_BitVector"
     <li>to_std_logic_vector - calls "to_StdLogicVector"
      <li>to_std_ulogic_vector - calls "to_StdULogicVector"
</ul>
   <li> _reduce functions (and_reduce, nand_reduce, or_reduce ...) are defined
      These functions reduce a std_logic_vector (or ulogic) to a single bit.
      In vhdl-2008 these will be unary "or", example "or "11011" = '1'"
   <li> "vector" and "std_ulogic" operations are defined.  These will perform a
      boolean operation of a vector. <br>Example:<br>
      <b>"1" xor "1010" = "0101";</b>
   <li> "\??\" function is defined for "std_ulogic" ("??" operator is release)
      <b>if (\??\('1')) then -- will return a "true"</b>
   <li> READ and WRITE procedures for "std_logic_vector", "std_ulogic_vector"
      and "std_ulogic" are defined.
   <li> HREAD and HWRITE (Hex read and write) for std_logic_vector
      and std_ulogic_vector.  These are more "forgiving" than the ones
      originally from "std_logic_textio"
   <li> OREAD and OWRITE (octal read and write) for std_logic_vector
      and std_ulogic_vector.  These are more "forgiving" than the ones
      originally from "std_logic_textio"
   <li> BREAD and BWRITE (binary read and write, same as "READ" and "WRITE" for
      std_logic_vector and std_ulogic_vector.
   <li> to_string function - Converts a "std_ulogic", "std_logic_vector" or
      "std_ulogic_vector" types into a string.<br>
      Example: <br>
      <b>assert (slv = "101") report "result was " & to_string(slv) severity note;</b>
   <li> to_hstring and to_ostring function (std_(u)logic_vector to hex or octal
      string)
</ul>

Please send feedback to <em>David W. Bishop
<a href="mailto:dbishop@vhdl.org">dbishop@vhdl.org</a></em>. &nbsp

</font>
</body>
</html>
