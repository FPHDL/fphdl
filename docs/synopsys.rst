Synopsys
########

Tested with Synopsys 2006.06 sp4, you may be able to use earlier versions,
but if you do make sure that you are using the "Presto" compiler.

To load, The easiest way is to add the following lines into your compile script
(You need only load the packages you need):

.. code-block:: tcl
   
   define_design_lib ieee_proposed -path ./ieee_proposed
   analyze -w ieee_proposed -f vhdl standard_additions_c.vhdl
   analyze -w ieee_proposed -f vhdl std_logic_1164_additions.vhdl
   analyze -w ieee_proposed -f vhdl numeric_std_additions.vhdl
   analyze -w ieee_proposed -f vhdl numeric_std_unsigned_c.vhdl
   analyze -w ieee_proposed -f vhdl math_utility_pkg.vhdl
   analyze -w ieee_proposed -f vhdl fixed_pkg_c.vhdl
   analyze -w ieee_proposed -f vhdl float_pkg_c.vhdl
   # analyze -w work -f vhdl float_synth.vhdl

Included in this <a href="synopsys.zip">ZIP file</a> are the following packages (only include the ones you need):
<ul>library ieee_proposed;
<li>use ieee_proposed.standard_additions.all; -- Additions to packages standard.std
<li>use ieee_proposed.std_logic_1164_additions.all; -- Additions to std_logic_1164
<li>use ieee_proposed.numeric_std_additions.all; -- Additions to numeric_std
<li>use ieee_proposed.numeric_std_unsigned.all;  -- Package to do unsigned math with std_logic_vectors, similar to the (sic) ieee.std_logic_unsigned package.
<li>use ieee_proposed.math_utiliti_pkg.all; -- Types for the fixed and float packages
<li>use ieee_proposed.fixed_pkg.all; -- Fixed point package
<li>use ieee_proposed.float_pkg.all; -- Floating point package
</ul>
The "README" file in the ZIP file will give you a list of the new functions.

See the README for an explination of the new functions in these packages.
You will also want to look at the
<a href="http://www.vhdl.org/fphdl/Fixed_ug.pdf">Fixed point docuementation</a> and the
<a href="http://www.eda.org/fphdl/Float_ug.pdf">Floating point docuementation</a>.


.. NOTE::
   
    * Synopsys doesn't accept the 1076.6 "-- rtl_synthesis off" metacomment.  I placed "-- pragma synthesis_off" metacomments around these. &nbsp
    * When Synopsys sees fixed_pkg'instance_name it dies on elaboration.
      Replaced with "fixed_pkg" (and "float_pkg") where necessary.
    * Same problem with "integer'image" and "real'image" - commented out.
    * I had to replace the "match_logic_table" and "no_match_logic_table" with a logical equivilent.  This was done in "std_logic_1164_additions" and in "fixed_pkg_c".
