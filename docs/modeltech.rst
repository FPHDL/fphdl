Modeltech / QuestaSim
#####################

Tested with Modeltech/Questasim 6.5b

When you compile you will get a warning:
(vcom-1246) Range 0 downto 1 is null.
To suppress this warning compile with "-suppress 1236"
In the MTI install you will find a premapped library called
"floatfixlib".  This contains an old version of "fixed_pkg" and "float_pkg".
The versions in this release are newer.

To compile:  source the "compile.mti" script.  This will create the
IEEE_PROPOSED VHDL library.

See the README for an explination of the new functions in these packages.
