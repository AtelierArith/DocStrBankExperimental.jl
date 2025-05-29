```
XPRSgetdirs(prob, indices, prios, branchdirs, uppseudo, downpseudo)::ndir, indices, prios, branchdirs, uppseudo, downpseudo
```

Used to return the directives that have been loaded into a matrix.

Priorities, forced branching directions and pseudo costs can be returned. If called after presolve, `XPRSgetdirs` will get the directives for the presolved problem.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `indices::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `ndir` containing the column numbers (`0`, `1`, `2`,...) or negative values corresponding to special ordered sets (the first set numbered `-1`, the second numbered `-2`,...). You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `prios::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array of length `ndir` containing the priorities for the columns and sets, where columns/sets with smallest priority will be branched on first. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `branchdirs::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Character array of length `ndir` specifying the branching direction for each column or set: Uthe entity is to be forced up; Dthe entity is to be forced down; Nnot specified. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `uppseudo::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ndir` containing the up pseudo costs for the columns and sets. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `downpseudo::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of length `ndir` containing the down pseudo costs for the columns and sets. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `ndir::Int32`: Pointer to an integer where the number of directives will be returned.
  * `indices::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `ndir` containing the column numbers (`0`, `1`, `2`,...) or negative values corresponding to special ordered sets (the first set numbered `-1`, the second numbered `-2`,...).
  * `prios::Union{Nothing,AbstractVector{Int32}}`: Integer array of length `ndir` containing the priorities for the columns and sets, where columns/sets with smallest priority will be branched on first.
  * `branchdirs::Union{Nothing,AbstractVector{Cchar}}`: Character array of length `ndir` specifying the branching direction for each column or set: Uthe entity is to be forced up; Dthe entity is to be forced down; Nnot specified.
  * `uppseudo::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ndir` containing the up pseudo costs for the columns and sets.
  * `downpseudo::Union{Nothing,AbstractVector{Float64}}`: Double array of length `ndir` containing the down pseudo costs for the columns and sets.

See also the documentation of the correponding function [XPRSgetdirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdirs.html) in the C API.
