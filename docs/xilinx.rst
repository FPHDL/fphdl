Xilinx ISE
##########

Tested with Xilinx M9.1i sp1

Go through "new project" and add the files to the project.
Go to the "Source Libraries" tab under "Sources"
Click on a blank area of that window, Select "New Source"
Select "VHDL Library", enter the name "ieee_proposed" and hit "Finish".
Select "math_utility_pkg.vhdl", "fixed_pkg_c.vhdl", and "float_pkg_c.vhdl"
one at a time and move them into "ieee_proposed" library.

Click on "Synthesis" and select "Run".


Things Xilinx m9.1i didn't like about these packages:
1) Didn't like the "alias" statements on functions and type.  Had to comment
these out or replace them with subtypes.
2) 'instance_name - Doesn't like this attribute, replace with package name.
3) "to_stdlogicvector(to_suv(arg))" shows as a type conversion error, replace
with casting "std_logic_vector()"
4) "to_stdulogicvector(arg)" shows as a type conversion error, replace with
casting "std_ulogic_vector()"

After fixing everything, it gave me the error:
INTERNAL_ERROR:Xst:cmain.c:3111:1.8.6.1 -  To resolve this error, please
consult the Answers Database and other online resources at
http://support.xilinx.com 

Which according to Xilinx has to do with the loops in my synthesis testcase,
and not the packages.  This is a "use at your own risk" one I guess.  I would
recommend Synplicity, which seems to work much better.  Xilinx has said that
they plan to fix this problem in version 9.2.
