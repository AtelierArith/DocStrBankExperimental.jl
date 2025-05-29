```
gradient(() -> loss(), ps::Params) -> Grads
```

Gradient with implicit parameters. Takes a zero-argument function, and returns a dictionary-like container, whose keys are arrays `x in ps`.

See also [`withgradient`](@ref) to keep the value `loss()`.

```jldoctest; setup=:(using Zygote)
julia> x = [1 2 3; 4 5 6]; y = [7, 8]; z = [1, 10, 100];

julia> g = gradient(Params([x, y])) do
         sum(x .* y .* z')
       end
Grads(...)

julia> g[x]
2×3 Matrix{Float64}:
 7.0  70.0  700.0
 8.0  80.0  800.0

julia> haskey(g, z)  # only x and y are parameters
false
```
