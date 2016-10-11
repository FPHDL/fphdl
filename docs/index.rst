VHDL-2008 Support Library
#########################

These packages were designed as a bridge between VHDL-93 and VHDL-2008. I
replicated as many of the new functions as possible. Note that all of these
packages are design to be synthesizable in VHDL-93. So, as long as you stick
to the subsets defined in the "README" files for the various vendors you should
be able to take your code through the entire flow.

VHDL-2008 is finally getting some traction. What started out as just a fixed
and floating point package got merged into the VHDL LRM. On this page you will
find definitions of the functions available in the VHDL-2008 libraries. You will
also find VHDL-93 compatible code for those that do not yet have access to
VHDL-2008 compilers.

There is a Fixed Point user's guide and a Floating Point user's guide. Please
check the Fixed and floating point FAQ (NEW!) if you have any quesiton.

The VHDL-2008 packages will eventually be included in your vendor's environment.
In some cases I have found that they may be encrypted due to IEEE rules. The
packages available on this page are NOT the released packages, but VHDL-93
versions of those packages, which I published BEFORE the release of the LRM.
They are free of copyright restrictions, and may be used for whatever purpose is
needed.

VHDL-93 versions of the VHDL-2008 packages
******************************************

+----------------------------------+----------------------------------+-------------------------------+
| Description                      | File                             | User Guide                    |
+==================================+==================================+===============================+
| Additions to std.standard        | standard_additions_c.vhdl        | user's guide                  |
+----------------------------------+----------------------------------+-------------------------------+
| New package std.env              | env_c.vhdl                       |                               |
+----------------------------------+----------------------------------+-------------------------------+
| Additions to std.textio          | standard_textio_additions_c.vhdl | (user's guide)                |
+----------------------------------+----------------------------------+-------------------------------+
| Additions to ieee.std_logic_1164 | std_logic_1164_additions.vhdl    | (user's guide)                |
+----------------------------------+----------------------------------+-------------------------------+
| Additions to ieee.numeric_std    | numeric_std_additions.vhdl       | (user's guide)                |
+----------------------------------+----------------------------------+-------------------------------+
| New package numeric_std_unsigned | numeric_std_unsigned_c.vhdl      | (user's guide)                |
+----------------------------------+----------------------------------+-------------------------------+
| New package fixed_float_types    | fixed_float_types_c.vhdl         |                               |
+----------------------------------+----------------------------------+-------------------------------+
| New package fixed_pkg            | fixed_pkg_c.vhdl                 | (Fixed Point user's guide)    |
+----------------------------------+----------------------------------+-------------------------------+
| New package float_pkg            | float_pkg_c.vhdl                 | (Floating Point user's guide) |
+----------------------------------+----------------------------------+-------------------------------+

.. ZIP file of all the packages (updated 09/2010)

I use this code in most of my designs. Many times I find that I have to modify
the code slightly in some tools, so I made this list. Included in the "source
code" section for each tool is source code specifically debugged for that
particluar tool. Click on the "documentation" link to see what changes I had to
make, and how to use this code in the specific tool.

Tool specifc modifications
**************************

+--------------------------------+----------+-------+
| Vendor / Tool                  | ZIP File | Notes |
+================================+==========+=======+
| :doc:`Altera Quartus <altera>` |          |       |
+--------------------------------+----------+-------+

.. 
   Altera	Source code	Documentation
   Cadence ncvhdl	Source code	Documentation
   Cadence RC (new)	Source code	Documentation
   Modeltech	Source code	Documentation
   Synopsys	Source code	Documentation
   Synplicity	Source code	Documentation
   Xilinx 11.1	Source code	Documentation
   Xilinx 9.1	Source code (old)	Documentation
   VCS	Source code	Documentation
   Spectrum 2009a	Source code	Documentation
	 
.. TODO:.
   Aldec

Some helpful code to go with these packages
*******************************************

 * fixed_noresize.vhdl
      Similar to ``fixed_pkg``, however this version uses the same rules that
      ``numeric_std`` does for the size of the result. This is done by calling
      the function in ``fixed_pkg`` and resizing the result.
 * float_noround_pkg.vhdl
      Similar to ``float_pkg``, however this version turns off all of the IEEE
      rounding and overflow, and defaults to a 26 bit floating point number.
      This package saves off 1/3 of the logic needed for full 32 bit floating
      point.
 * fixed_synth.vhdl
      Synthesis testcase for the fixed point package.
 * test_fixed_synth.vhdl
      Testbench for the fixed point synthesis testcase.
 * float_synth.vhdl
      Synthesis testcase for the floating point package.
 * test_float_synth.vhdl
      Testbench for the floating point synthesis package
 * Matrix Math package
      for type REAL which has a user guide (Done in conjunction with IEEE 1076.1 VHDL-AMS)
 * Testbenches to verify an implimentation of VHDL-2008.





.. toctree::
   :hidden:
   
   new
   additions
   tools
