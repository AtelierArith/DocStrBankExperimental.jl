```
update!(lk::Link, x; s::Symbol=:sta)
update!(lk::Link, arg::Args)
update!(name::Symbol, ....)
```

Update an actor's internal state `s` with `args...`.

# Arguments

  * an actor `lk::Link` or `name::Symbol` (if registered),
  * `x`: value/variable to update the choosen state with,
  * `arg::Args`: arguments to update,
  * `s::Symbol`: can be one of `:sta`, `:dsp`, `:arg`, `:self`, `:name`.

*Note:* If you want to update the stored arguments to the  behavior function with `s=:arg`, you must pass an [`Args`](@ref)  to `arg`. If `Args` has keyword arguments, they are merged  with existing keyword arguments to the behavior function.

# Example

```julia
julia> update!(fact, 5)       # note that fact is in state dispatch
YAActL.Update{Int64}(:sta, 5)

julia> call!(fact, 5)         # call it with 5
10

julia> update!(fact, Args(0, u=5));  # update arguments

julia> call!(fact, 5)         # add the last result, 5 and u=5
20
```
