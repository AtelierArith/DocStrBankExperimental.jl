```
Actor([lp::LinkParams], bhv::Function, args1...; kwargs...)
Actor(pid::Int, bhv::Function, args1...; kwargs...)
```

Create a new actor. Start a task listening to messages `msg`  sent over the returned self and executing `bhv(args1..., msg; kwargs...)`  for each message. The actor stops if sent [`Stop()`](@ref).

# Arguments

  * `[lp::LinkParams]`: parameters for creating the actor,
  * `pid::Int`: process `pid` to create the actor on, this can    also be given with `lp`,
  * `bhv`: a function implementing the actor's behavior,
  * `args1...`: first arguments to `bhv` (without possible `msg` arguments),
  * `kwargs...`: keyword arguments to `bhv`.

# Returns

  * a [`Link`](@ref) to a created actor.

see also: [`LinkParams`](@ref)

# Example

```julia
julia> using YAActL, .Threads

julia> act1 = Actor(threadid)               # start an actor who gives its threadid
Channel{Message}(sz_max:32,sz_curr:0)

julia> call!(act1)                          # call it
1
```
