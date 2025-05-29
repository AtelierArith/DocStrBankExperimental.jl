```
query!(lk::Link, from::Link, s::Symbol)
query!(lk::Link, s::Symbol; timeout::Real=5.0)
query!(name::Symbol, ....)
```

Ask the `lk` actor to send a [`Response`](@ref) message to `from` with an internal state variable `s`. 

If `from` is omitted, `query!` blocks and returns the response. In that case there is a `timeout`.

  * `s::Symbol` can be one of `:sta`, `:res`, `:bhv`, `:dsp`.

# Examples

```julia
julia> f(x, y; u=0, v=0) = x+y+u+v  # implement a behavior
f (generic function with 1 method)

julia> fact = Actor(f, 1)     # start an actor with it
Channel{Message}(sz_max:32,sz_curr:0)

julia> cast!(fact, 1)         # cast a second parameter to it
YAActL.Cast{Tuple{Int64}}((1,))

julia> query!(fact, :res)     # query the result
2

julia> query!(fact, :bhv)     # query the behavior
f (generic function with 1 method)

julia> set!(fact, state)      # set dispatch mode
YAActL.Update{Dispatch}(:dsp, state)

julia> query!(fact, :dsp)     # query the dispatch mode
state::Dispatch = 1

julia> update!(fact, 10)      # update the state
YAActL.Update{Int64}(:sta, 10)

julia> query!(fact)           # query the state variable
10

julia> call!(fact, 1)
11
```
