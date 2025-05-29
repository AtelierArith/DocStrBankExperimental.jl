```
diaghessian(f, args...) -> Tuple
```

Diagonal part of the Hessian. Returns a tuple containing, for each argument `x`, `h` of the same shape with `h[i] = Hᵢᵢ = ∂²y/∂x[i]∂x[i]`.  The original evaluation `y = f(args...)` must give a real number `y`.

For one vector argument `x`, this is equivalent to `(diag(hessian(f,x)),)`. Like [`hessian`](@ref) it uses ForwardDiff over Zygote. 

!!! warning
    For arguments of any type except `Number` & `AbstractArray`, the result is `nothing`.


# Examples

```jldoctest; setup=:(using Zygote, LinearAlgebra)
julia> diaghessian(x -> sum(x.^3), [1 2; 3 4])[1]
2×2 Matrix{Int64}:
  6  12
 18  24

julia> Diagonal(vec(ans)) == hessian(x -> sum(x.^3), [1 2; 3 4])  # full Hessian is diagonal
true

julia> diaghessian((x,y) -> sum(x .* y .* y'), [1 22; 333 4], [0.5, 0.666])  # two array arguments
([0.0 0.0; 0.0 0.0], [2.0, 8.0])

julia> diaghessian(atan, 1, 2)  # two scalar arguments
(-0.16, 0.16)

julia> hessian(xy -> atan(xy[1], xy[2]), [1, 2])  # full Hessian is not diagonal
2×2 Matrix{Float64}:
 -0.16  -0.12
 -0.12   0.16
```
