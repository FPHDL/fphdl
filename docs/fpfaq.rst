<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML//EN">
<html><head><title>Fixed and Floating point VHDL FAQ</title>
<!-- Changed by: , 07-Oct-2010 -->
  <meta name="description" content="Fixed and Floating point VHDL frequently asked questions">
  <meta name="author" content="dbishop@vhdl.org">
<meta name=keywords content="ASIC, FPGA, VHDL, VHDL-2008">
<meta name=identifier-url content="http://vhdl.org/fphdl/fpfaq.html">
<meta name=distribution content=Global>
<meta name=rating content=General>
<meta name=copyright content=>
<meta name=resource-type content=document>
<meta name=reply-to content="dbishop@vhdl.org">
<meta name=robots content=all>
<meta name=language content=en>
<meta http-equiv=content-type content=text/html; charset=iso-8859-1>
</head>
<body bgcolor="#FFFFFF" text="#000000" link="#0000FF" vlink="#007F00">
<p align="right"><font face=Arial color=#cecece size=6 Helvetica, sans-serif>
<b><i>Fixed and Floating point VHDL FAQ</i></b></font></p>
<font face=Arial size=2 Helvetica, sans-serif>
<p>
What follows are frequently asked questions about the fixed and floating
point VHDL packages. &nbsp;  VHDL-93 source code can be found on the
<a href="http://vhdl.org/fphdl/index.html">VHDL-2008 support library page</a>.
&nbsp;
You will find these packages built into several implimentations of VHDL. &nbsp;
</p>
<h4>
What synthesis results can I expect?
</h4>
<p>
Under the hood, all of the fixed and floating point functions call functions
from the "numeric_std" package. &nbsp;  Much work was done to make sure that
these algorithms would be as fast as possible. &nbsp;   You can expect a fixed
point multiply to be just as fast as an UNSIGNED multiply.  &nbsp;  Floating
point gives you about 3X overhead. &nbsp; However you get much more accurate
results. &nbsp;  My best results have been gotten by mixing the two.
</p>
<h4>
Where are the shift operators? </h4>
<p>
You don't need them.  Use the "scalb" function.  This function works as
follows:
<pre>
variable uf1 : ufixed (5 downto 0);
variable uf2 : ufixed (4 downto -1);
...
uf2 := scalb (uf1, -1);  -- shift right by 1
</pre>
The nice thing about this function is that you don't loose any data. &nbsp;
Note that under the hood, for some synthesis tools, this function is
implimented with shift operators.  Standard shift operators are built into
VHDL-2008, but some vendors have not implemented them.
</p>
<h4>
Why can't I say "X &lt;= '0' &amp; Y;" to tack a '0' in front of
(or behind) a vector?
</h4>
<p>
The problem here is that the vector returned will be
"ufixed (integer'low to integer'low+Y'high)" or essentially 2**-32,000
(a VERY small number). &nbsp;
Instead, use the resize function:
<pre>
X &lt;= resize (Y, X'high, X'low);
</pre>
The resize function is used to all of the rouding in the fixed point package.
</p>
<h4>
These sizing rules are a pain.  &nbsp; Why can't these packages work more
like numeric_std?</h4>
<p>
The sizing was done so that you never need to round, thus removing one addition
stage, and making the results run faster.  &nbsp;
For the applications where this is just a pain, I've created
<a href="fixed_noresize.vhdl">fixed_noresize.vhdl</a>. &nbsp;
This package creates the types "fixedu" and "fixeds" (which are similar to
"ufixed" and "sfixed"). However these new types have the same sizing rules
as numeric_std UNSIGNED and SIGNED.
</p>
<p>Note that there is also an "add_carry" procedure in the
<a href="Fixed_ug.pdf">fixed point package</a> for fixed point
accumulators, which can be used like this:
<pre>
variable uf3: ufixed (3 downto -2);
constant one : ufixed (0 downto 0) := "1";
...
add_carry (
  L => uf3,
  R => one,
  result => uf3,
  c_in => '0',
  c_out => open);
</pre>
This procedure will return a result which is the "widest" of the inputs. &nbsp;
Overflow will show up in the "c_out" output.
</p>
<h4>
My floating point divider (or other function) is slow, what can I do about it?
</h4>
<p>
Yes, it will be, a floating point divider is lots of logic.  &nbsp;
You will need to pipeline these functions.   &nbsp;
Some synthsis tools will do this for you automatically.   &nbsp;
Others will make you pipline them manually.  &nbsp;
I have already created pipelined versions of many of them.
</p>
<h4>
How do you convert unsigned fixed point (ufixed)
into signed fixed point (sfixed)?
</h4>
<p>
There is a function "to_sfixed(ufixed)" which increases the size of the output
by 1 (the sign bit). &nbsp;
The "to_ufixed(sfixed)" function returns a vector of the same size as the
input. &nbsp;

</p>
<h4>
What happened to the "math_utility_pkg" package?</h4>
It got replaced with the
<a href="fixed_float_types_c.vhdl">fixed_float_types package</a>
during the final edits of the VHDL-2008 LRM.  &nbsp;
Some older implimentations of these packages (like the ones built into the
floatfixlib library in version 6.* of Modeltech) still use it. &nbsp;
The types in these two packages are identical.
<p>
<h4>
Why does the "break_number" return an incorrect result?</h4>
This has to do with how the floating point number is encoded. The exponent is
biased by -1.   Thus if you take every result and multiply it by 2 you will get
the correct answer.  The "break_number" routine was designed to be a synthesis pass
through, creating no logic.  It is up to the next function to fix the bias.
<h4>
What bugs have been found?</h4>
<p>
So far:
<ul>
<li>The <b>add_carry</b> for both the "sfixed" and "ufixed" types has a bug in
the "c_out" output.   "c_out" will be incorrect because of this bug.
This function is fixed in the <a href="fixed_pkg_c.vhdl">latest version</a>
</li>
<li>The <b>to_float (sfixed)</b> function will return the wrong result if the
"sfixed" value is the largest possible negative number ("100000"). &nbsp;
That function is fixed in the <a href="float_pkg_c.vhdl">latest version</a>.
</li>
<li>The <b>to_float (ufixed)</b> funciton will return the wrong result if the
decimal width of the number is larger than can be held in the exponent of the
result. &nbsp;  This is only a problem with denormal numbers. &nbsp;
That function is fixed in the <a href="float_pkg_c.vhdl">latest version</a>.
</li>
<li>The documented sizing rules for the fixed point <b>reciprocal</b>
 function in
the VHDL-2008 LRM is wrong. &nbsp; It is corrected in
<a href="Fixed_ug.pdf">Fixed point users guide</a>
</li>
</ul>
<p>
Need some help with this code?
Drop me an <a href="mailto:dbishop@vhdl.org">e-mail</a>, maybe I can help.<br>
<b>My company will also allow me to consult for you.</b><br />
</p>
<p>
This web page is brought to you by the
<a href="http://eda.org"
target="_top">EDA Industry Working Groups</a> and 
<a href="http://www.accellera.org/home"
target="_top">Accellera</a>.
</p>
</font>
</body>
</html>