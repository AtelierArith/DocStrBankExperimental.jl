```
XPRSgetindex(prob, type, name)::index
```

Returns the index for a specified row or column name.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `type::Integer`: XPRS*NAMES*ROW`(=1)` if row index is required; XPRS*NAMES*COLUMN`(=2)` if column index is required; XPRS*NAMES*SET`(=3)` if set index is required; XPRS*NAMES*PWLCONS`(=4)` if piecewise linear constraint index is required; XPRS*NAMES*GENCONS`(=5)` if general constraint index is required; XPRS*NAMES*OBJECTIVE`(=6)` if objective index is required; XPRS*NAMES*USERFUNC`(=7)` if user function index is required; XPRS*NAMES*INTERNALFUNC`(=8)` if an internal function index is required.
  * `name::Union{Nothing,AbstractString}`: Null terminated string.

# Return value

  * `index::Int32`: Pointer of the integer where the row or column index number will be returned.

See also the documentation of the correponding function [XPRSgetindex](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetindex.html) in the C API.
