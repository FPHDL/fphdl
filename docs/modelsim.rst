Modeltech / ModelSim
####################

Tested with Modeltech 6.2e

To compile:  source the "compile.mti" script.  This will create the
IEEE_PROPOSED VHDL library.  The ZIP file contains VHDL-93 compatable versions
of several of the new packages.  Included in this <a href="modelsim.zip">ZIP file</a> are the following packages:
<ul>library ieee_proposed;
<li>use ieee_proposed.standard_additions.all; -- Additions to packages standard.std
<li>use ieee_proposed.standard_textio.all; -- Additions to packages standard.textio
<li>use ieee_proposed.env.all;  -- New "env" package
<li>use ieee_proposed.std_logic_1164_additions.all; -- Additions to std_logic_1164
<li>use ieee_proposed.numeric_std_additions.all; -- Additions to numeric_std
<li>use ieee_proposed.numeric_std_unsigned.all;  -- Package to do unsigned math with std_logic_vectors, similar to the (sic) ieee.std_logic_unsigned package.
<li>use ieee_proposed.math_utiliti_pkg.all; -- Types for the fixed and float packages
<li>use ieee_proposed.fixed_pkg.all; -- Fixed point package
<li>use ieee_proposed.float_pkg.all; -- Floating point package
</ul>

See the README for an explination of the new functions in these packages.
You will also want to look at the
<a href="http://www.vhdl.org/vhdl-200x/vhdl-200x-ft/packages/Fixed_ug.pdf">Fixed point docuementation</a> and the
<a href="http://www.eda.org/vhdl-200x/vhdl-200x-ft/packages/Float_ug.pdf">Floating point docuementation</a>.

.. NOTE::
   When you simulation, you may need to use the ``-novopt`` option. Otherwise
   some of the alias won't get seen correctly.
