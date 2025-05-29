```
XPRSgetcutlist(prob, cuttype, interp, maxcuts, cutind)::ncuts, cutind
```

Retrieves a list of cut pointers for the cuts active at the current node.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `cuttype::Integer`: User defined type of the cuts to be returned.
  * `interp::Integer`: Way in which the cut type is interpreted: -1get all cuts; 1treat cut types as numbers; 2treat cut types as bit maps - get cut if any bit matches any bit set in `cuttype`; 3treat cut types as bit maps - get cut if all bits match those set in `cuttype`.
  * `maxcuts::Integer`: Maximum number of cuts to be retrieved.
  * `cutind::Union{XPRSallocatable,AbstractVector{Ptr{Cvoid}}}`: Array of length `maxcuts` where the pointers to the cuts will be returned. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you.

# Return values

  * `ncuts::Int32`: Pointer to the integer where the number of active cuts of type `cuttype` will be returned.
  * `cutind::AbstractVector{Ptr{Cvoid}}`: Array of length `maxcuts` where the pointers to the cuts will be returned.

See also the documentation of the correponding function [XPRSgetcutlist](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcutlist.html) in the C API.
