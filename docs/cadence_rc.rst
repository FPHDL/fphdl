Cadence RC
##########

Checked with RC version 11.20

To Compile:
just run "compile.rc"

Notes:
Had to remove the "match_table".  This gave me the error:
Error   : Incompatible bitwidths in assignment. [CDFG-283] [elaborate]
        : Width of target 'match_logic_table' (1) doesn't match the width of the assigned value (81) in file 'fixed_pkg_c.vhdl' on line 1595.
        : Use 'set_attribute hdl_vhdl_assign_width_mismatch true /' to allow such assignments with mismatching widths of lhs and rhs.

So, I set the variable, and still had the error....
Replaced it with an "rtl" version of the match table.  In synthsis it will behave
the same way as rtl, but not in simulaiton.

Version 11.20 hung on the floating point package.  I reported this to Cadence,
and they said to change the synthesis effort to "medium" and use verion 12.10.

To run these testcases:

rc -f fixed_synth.tcl
rc -f float_synth.tcl
