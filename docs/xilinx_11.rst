Xilinx ISE
##########

Tested with Xilinx M11.2i

Go through "new project" and add the files to the project.
When the "Adding Source files..." windows comes up, change the library
for "fixed_float_types.vhdl", "fixed_pkg_c.vhdl" and "float_pkg_c.vhdl" to
"ieee_porposed"

Click on "Synthesis" and select "Run".

I had to really fight to get these packages to synthesize in this tool. I
could not check everything, so "use at your own risk".  For a real Xilinx
project I would use still Synplicity or Leonardo.  However, I was able to
get both my fixed and floating point testcases (with some modification)
to place and route.  This is a major improvement over M9.1i

Things Xilinx m11.1i didn't like about these packages:
1) 'instance_name showed as a syntax error, replace with package name
2) "to_stdlogicvector(to_suv(arg))" shows as a type conversion error, replace
with casting "std_logic_vector()"
3) Did not like any of the fixed point division routines,
had to comment them out.
4) Had to comment out the "?=" routines, XST could not deal with that syntax.
