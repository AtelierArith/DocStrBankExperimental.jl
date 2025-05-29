```
hessian(f, x)
```

Construct the Hessian `∂²f/∂x²`, where `x` is a real number or an array, and `f(x)` is a real number. When `x` is an array, the result is a matrix `H[i,j] = ∂²f/∂x[i]∂x[j]`, using linear indexing `x[i]` even if the argument is higher-dimensional.

This uses forward over reverse, ForwardDiff over Zygote, calling `hessian_dual(f, x)`. See [`hessian_reverse`](@ref) for an all-Zygote alternative.

See also [`diaghessian`](@ref) to compute only the diagonal part.

# Examples

```jldoctest; setup=:(using Zygote)
julia> hessian(x -> x[1]*x[2], randn(2))
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> hessian(x -> sum(x.^3), [1 2; 3 4])  # uses linear indexing of x
4×4 Matrix{Int64}:
 6   0   0   0
 0  18   0   0
 0   0  12   0
 0   0   0  24

julia> hessian(sin, pi/2)
-1.0
```
