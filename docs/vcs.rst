VCS
###

Tested with VCS C-2009.06

Textio issues:
VCS reports time with capital letters.  So instead of "5 ns" you will get
"5 NS".  It also doesn't know what an NBSP is (it's in the spec, but not in
VCS).  'instance_name works, but you don't get a seperator at the end.
(not reported).
The Textio "NBSP" does not appear to be recognized by VCS. (not reported)

This version does not seem to like the floating point packages, however
previous versions did.
