```
XPRSgetrows(prob, start, colind, colcoef, maxcoefs, first, last)::start, colind, colcoef, ncoefs
```

Returns the nonzeros in the constraint matrix for the rows in a given range.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `start::AbstractVector{Int32}`: Integer array which will be filled with the indices indicating the starting offsets in the `colind` and `colcoef` arrays for each requested row.
  * `colind::AbstractVector{Int32}`: Integer arrays of length `maxcoefs` which will be filled with the column indices of the nonzero elements for each row.
  * `colcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` which will be filled with the nonzero element values.
  * `maxcoefs::Integer`: Maximum number of elements to be retrieved.
  * `first::Integer`: First row in the range.
  * `last::Integer`: Last row in the range.

# Return values

  * `start::AbstractVector{Int32}`: Integer array which will be filled with the indices indicating the starting offsets in the `colind` and `colcoef` arrays for each requested row.
  * `colind::AbstractVector{Int32}`: Integer arrays of length `maxcoefs` which will be filled with the column indices of the nonzero elements for each row.
  * `colcoef::AbstractVector{Float64}`: Double array of length `maxcoefs` which will be filled with the nonzero element values.
  * `ncoefs::Int32`: Pointer to the integer where the number of nonzero elements in the selected rows will be returned.

See also the documentation of the correponding function [XPRSgetrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrows.html) in the C API.
