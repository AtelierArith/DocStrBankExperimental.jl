```
XPRSmsaddjob(prob, description, ninitial, colind, initial, nintcontrols, intcontrolid, intcontrolval, ndblcontrols, dblcontrolid, dblcontrolval, data)::prob
```

Adds a multistart job to the multistart pool

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `description::Union{Nothing,AbstractString}`: Text description of the job.
  * `ninitial::Integer`: Number of initial values to set.
  * `colind::AbstractVector{Integer}`: Indices of the variables for which to set an initial value.
  * `initial::AbstractVector{Number}`: Initial values for the variables for which to set an initial value.
  * `nintcontrols::Integer`: Number of integer controls to set.
  * `intcontrolid::AbstractVector{Integer}`: The indices of the integer controls to be set.
  * `intcontrolval::AbstractVector{Integer}`: The values of the integer controls to be set.
  * `ndblcontrols::Integer`: Number of double controls to set.
  * `dblcontrolid::AbstractVector{Integer}`: The indices of the double controls to be set.
  * `dblcontrolval::AbstractVector{Number}`: The values of the double controls to be set.
  * `data::Any`: Job specific user context pointer to be passed to the multistart callbacks.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSmsaddjob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmsaddjob.html) in the C API.
