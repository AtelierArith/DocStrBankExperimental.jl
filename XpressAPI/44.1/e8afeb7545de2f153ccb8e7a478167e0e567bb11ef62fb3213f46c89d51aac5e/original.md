```
XPRSgetrowtype(prob, rowtype, first, last)::rowtype
```

Returns the row types for the rows in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `rowtype::Union{XPRSallocatable,AbstractVector{Cchar}}`: Character array of length `last-first+1` characters where the row types will be returned: Nindicates a free constraint; Lindicates a `<=` constraint; Eindicates an = constraint; Gindicates a `>=` constraint; Rindicates a range constraint. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.
  * `first::Integer`: First row in the range.
  * `last::Integer`: Last row in the range.

# Return value

  * `rowtype::AbstractVector{Cchar}`: Character array of length `last-first+1` characters where the row types will be returned: Nindicates a free constraint; Lindicates a `<=` constraint; Eindicates an = constraint; Gindicates a `>=` constraint; Rindicates a range constraint.

See also the documentation of the correponding function [XPRSgetrowtype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrowtype.html) in the C API.
