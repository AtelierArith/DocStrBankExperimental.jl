```
XPRS_bo_getlasterror(bo, maxbytes)::msgcode, msg, nbytes
```

Returns the last error encountered during a call to the given branch object.

# Arguments

  * `bo::XPRSbranchobject`: The branch object.
  * `maxbytes::Integer`: The size of the character buffer `msg`.

# Return values

  * `msgcode::Int32`: Location where the error code will be returned.
  * `msg::AbstractString`: A character buffer of size `maxbytes` in which the last error message relating to the given branching object will be returned.
  * `nbytes::Int32`: The size of the required character buffer to fully return the error string.

See also the documentation of the correponding function [XPRS*bo*getlasterror](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_getlasterror.html) in the C API.
