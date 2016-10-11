Leonardo Spectrum
#################

Leonardo Spectrum (2009a)

Spectrum doesn't like the fixed point "divide" functions, so they are
commented out in this release. In order to get a divide to work you
will have to write your own divider.
I've also had to comment out the "alias" statement.

To run this code:
``spectrum -f fixed_synth.tcl``

For some reason Spectrum picks slow multipliers. You may need to use the
Modgen multipliers to meet timing.

Floating point functions, but the synthesis is very slow. I would recommand
that you use smaller accumulators with this tool.
