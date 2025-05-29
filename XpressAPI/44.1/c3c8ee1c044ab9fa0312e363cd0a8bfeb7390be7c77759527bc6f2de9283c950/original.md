```
XPRSloadmiqcqp(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub, nobjqcoefs, objqcol1, objqcol2, objqcoef, nqrows, qrowind, nrowqcoefs, rowqcol1, rowqcol2, rowqcoef, nentities, nsets, coltype, entind, limit, settype, setstart, setind, refval)::prob
```

Used to load a mixed integer quadratic problem with quadratic constraints into the Optimizer data structure.

Such a problem may have quadratic terms in its objective function as well as in its constraints. Integer, binary, partial integer, semi-continuous and semi-continuous integer variables can be defined, together with sets of type 1 and 2. The reference row values for the set members are passed as an array rather than specifying a reference row.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `probname::Union{Nothing,AbstractString}`: A string of up to MAXPROBNAMELENGTH characters containing a name for the problem.
  * `ncols::Integer`: Number of structural columns in the matrix.
  * `nrows::Integer`: Number of rows in the matrix (not including the objective row).
  * `rowtype::AbstractVector{Cchar}`: Character array of length `nrows` containing the row types: Lindicates a `<=` constraint (use this one for quadratic constraints as well); Eindicates an `=` constraint; Gindicates a `>=` constraint; Rindicates a range constraint; Nindicates a nonbinding constraint.
  * `rhs::AbstractVector{Number}`: Double array of length `nrows` containing the right hand side coefficients of the rows.
  * `rng::AbstractVector{Number}`: Double array of length `nrows` containing the range values for range rows.
  * `objcoef::AbstractVector{Number}`: Double array of length `ncols` containing the objective function coefficients.
  * `start::AbstractVector{Integer}`: Integer array containing the offsets in the `rowind` and `rowcoef` arrays of the start of the elements for each column.
  * `collen::AbstractVector{Integer}`: Integer array of length `ncols` containing the number of nonzero elements in each column.
  * `rowind::AbstractVector{Integer}`: Integer array containing the row indices for the nonzero elements in each column.
  * `rowcoef::AbstractVector{Number}`: Double array containing the nonzero element values; length as for `rowind`.
  * `lb::AbstractVector{Number}`: Double array of length `ncols` containing the lower bounds on the columns.
  * `ub::AbstractVector{Number}`: Double array of length `ncols` containing the upper bounds on the columns.
  * `nobjqcoefs::Integer`: Number of quadratic terms.
  * `objqcol1::AbstractVector{Integer}`: Integer array of size `nobjqcoefs` containing the column index of the first variable in each quadratic term.
  * `objqcol2::AbstractVector{Integer}`: Integer array of size `nobjqcoefs` containing the column index of the second variable in each quadratic term.
  * `objqcoef::AbstractVector{Number}`: Double array of size `nobjqcoefs` containing the quadratic coefficients.
  * `nqrows::Integer`: Number of rows containing quadratic matrices.
  * `qrowind::AbstractVector{Integer}`: Integer array of size `nqrows`, containing the indices of rows with quadratic matrices in them.
  * `nrowqcoefs::AbstractVector{Integer}`: Integer array of size `nqrows`, containing the number of nonzeros in each quadratic constraint matrix.
  * `rowqcol1::AbstractVector{Integer}`: Integer array of size `nqcelem`, where `nqcelem` equals the sum of the elements in `nrowqcoefs` (i.e. the total number of quadratic matrix elements in all the constraints).
  * `rowqcol2::AbstractVector{Integer}`: Integer array of size `nqcelem`, containing the second index for the quadratic constraint matrices.
  * `rowqcoef::AbstractVector{Number}`: Integer array of size `nqcelem`, containing the coefficients for the quadratic constraint matrices.
  * `nentities::Integer`: Number of binary, integer, semi-continuous, semi-continuous integer and partial integer entities.
  * `nsets::Integer`: Number of SOS1 and SOS2 sets.
  * `coltype::AbstractVector{Cchar}`: Character array of length `nentities` containing the entity types: Bbinary variables; Iinteger variables; Ppartial integer variables; Ssemi-continuous variables; Rsemi-continuous integer variables.
  * `entind::AbstractVector{Integer}`: Integer array of length `nentities` containing the column indices of the MIP entities.
  * `limit::AbstractVector{Number}`: Double array of length `nentities` containing the integer limits for the partial integer variables and lower bounds for semi-continuous and semi-continuous integer variables (any entries in the positions corresponding to binary and integer variables will be ignored).
  * `settype::AbstractVector{Cchar}`: Character array of length `nsets` containing the set types: 1SOS1 type sets; 2SOS2 type sets.May be `nothing` if not required.
  * `setstart::AbstractVector{Integer}`: Integer array containing the offsets in the `setind` and `refval` arrays indicating the start of the sets.
  * `setind::AbstractVector{Integer}`: Integer array of length `setstart[nsets]-1` containing the columns in each set.
  * `refval::AbstractVector{Number}`: Double array of length `setstart[nsets]-1` containing the reference row entries for each member of the sets.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSloadmiqcqp](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmiqcqp.html) in the C API.
