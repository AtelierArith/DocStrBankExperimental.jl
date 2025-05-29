```
XPRSsparsebtran(prob, val, ind)::val, ind, ncoefs
```

Post-multiplies a (row) vector provided by the user by the inverse of the current matrix.

Sparse version of XPRSbtran.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `val::AbstractVector{Float64}`: Double array of length ROWS containing the values which are to be post-multiplied by the basis inverse.
  * `ind::AbstractVector{Int32}`: Integer array of indices identifying the non-zero entries of `val`.

# Return values

  * `val::AbstractVector{Float64}`: Double array of length ROWS containing the values which are to be post-multiplied by the basis inverse.
  * `ind::AbstractVector{Int32}`: Integer array of indices identifying the non-zero entries of `val`.
  * `ncoefs::Int32`: Memory location where the number of non-zero entries is given.

See also the documentation of the correponding function [XPRSsparsebtran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsparsebtran.html) in the C API.
