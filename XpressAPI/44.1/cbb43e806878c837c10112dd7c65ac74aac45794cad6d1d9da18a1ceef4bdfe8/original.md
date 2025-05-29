```
XPRSslpgetcoefformula(prob, row, col, parsed, maxtypes, type, value)::factor, ntypes, type, value
```

Retrieve a single matrix coefficient as a formula split into tokens.

For a simpler version of this function see XSLPchgformula.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: Integer holding the row index for the coefficient.
  * `col::Integer`: Integer holding the column index for the coefficient.
  * `parsed::Integer`: Integer indicating whether the formula of the item is to be returned in internal unparsed format (`parsed`=0) or parsed (reverse Polish) format (`parsed`=1).
  * `maxtypes::Integer`: Maximum number of tokens to return, i.e. length of the `type` and `value` arrays.
  * `type::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array to hold the token types for the formula. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `value::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of values corresponding to `type`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `factor::Float64`: Address of a double precision variable to receive the value of the constant factor multiplying the formula in the coefficient.
  * `ntypes::Int32`: Number of tokens returned in type and value.
  * `type::Union{Nothing,AbstractVector{Int32}}`: Integer array to hold the token types for the formula.
  * `value::Union{Nothing,AbstractVector{Float64}}`: Double array of values corresponding to `type`.

See also the documentation of the correponding function [XPRSslpgetcoefformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcoefformula.html) in the C API.
