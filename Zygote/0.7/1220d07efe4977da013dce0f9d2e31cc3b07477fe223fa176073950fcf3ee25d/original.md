```
pullback(f, args...)
pullback(f, ::Params)
```

Returns the value of the function `f` and a back-propagator function, which can be called to obtain a tuple containing `∂f/∂x` for each argument `x`, the derivative (for scalar `x`) or gradient.

```julia
y, back = pullback(f, args...)
∇ = back(seed)
```

`back` must be called with a start value `seed` matching the output of `f(args...)`. If `f(args...)` returns a number, `seed` should be a number. If `f(args...)` returns an array, `seed` should be an equally-sized array.

See also [`withgradient`](@ref) to obtain the value and gradients in one call, and [`gradient`](@ref) for obtaining just the gradients.

```jldoctest; setup=:(using Zygote)
julia> y, back = pullback(*, 2.0, 3.0, 5.0);

julia> y
30.0

julia> back(1.0)
(15.0, 10.0, 6.0)

julia> back(2.0)
(30.0, 20.0, 12.0)

julia> y, back = pullback(x -> [x, x], 1.0);

julia> y
2-element Vector{Float64}:
 1.0
 1.0

julia> back([1.0, 1.0])
(2.0,)

julia> back([2.0, nothing])
(2.0,)
```
