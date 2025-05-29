```
XPRSslpgetccoef(prob, row, col, maxbytes)::factor, formula
```

**Deprecated**Use XPRSslpgetcoefstr instead.

Retrieve a single matrix coefficient as a formula in a character string. For a simpler version of this function see XPRSnlpgetformulastr.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: Integer holding the row index for the coefficient.
  * `col::Integer`: Integer holding the column index for the coefficient.
  * `maxbytes::Integer`: Maximum length of returned formula.

# Return values

  * `factor::Float64`: Address of a double precision variable to receive the value of the constant factor multiplying the formula in the coefficient.
  * `formula::AbstractString`: Character buffer in which the formula will be placed in the same format as used for input from a file.

See also the documentation of the correponding function [XPRSslpgetccoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetccoef.html) in the C API.
