Synplify
########

Tested with Synplify 2009.06

I tried the new "VHDL 2008 (beta)" VHDL option in this tool.   There were
major issues with function overloading, so don't use it.  Instead, include
the VHDL-93 package versions.   They all work find in this tool (no
modification needed).

To load, The easiest way is to add the following lines into your project file
(You need only load the packages you need):

.. code-block:: tcl
   
   add_file -vhdl -lib ieee_proposed "standard_additions_c.vhdl"
   add_file -vhdl -lib ieee_proposed "std_logic_1164_additions.vhdl"
   add_file -vhdl -lib ieee_proposed "numeric_std_additions.vhdl"
   add_file -vhdl -lib ieee_proposed "numeric_std_unsigned_c.vhdl"
   add_file -vhdl -lib ieee_proposed "math_utility_pkg.vhdl"
   add_file -vhdl -lib ieee_proposed "fixed_pkg_c.vhdl"
   add_file -vhdl -lib ieee_proposed "float_pkg_c.vhdl"

The "README" file in the ZIP file will give you a list of the new functions.

See the README for an explination of the new functions in these packages.
You will also want to look at the
<a href="http://www.vhdl.org/fphdl/Fixed_ug.pdf">Fixed point docuementation</a> and the
<a href="http://www.vhdl.org/fphdl/Float_ug.pdf">Floating point docuementation</a>.
