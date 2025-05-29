```
jacobian(f, args...) -> Tuple
```

For each array `a ∈ args` this returns a matrix with `Ja[k,i] = ∂y[k]/∂a[i]` where `y = f(args...)` is usually a vector. Arrays of higher dimension are treated like `vec(a)`, or `vec(y)` for output.

For scalar `x::Number ∈ args`, the result is a vector `Jx[k] = ∂y[k]/∂x`, while for scalar `y` all results have just one row.

With any other argument type, no result is produced, even if [`gradient`](@ref) would work.

This reverse-mode Jacobian needs to evaluate the pullback once for each element of `y`. Doing so is usually only efficient when `length(y)` is small compared to `length(a)`, otherwise forward mode is likely to be better.

See also [`withjacobian`](@ref), [`hessian`](@ref), [`hessian_reverse`](@ref).

# Examples

```jldoctest; setup=:(using Zygote)
julia> jacobian(a -> 100*a[1:3].^2, 1:7)[1]  # first index (rows) is output
3×7 Matrix{Int64}:
 200    0    0  0  0  0  0
   0  400    0  0  0  0  0
   0    0  600  0  0  0  0

julia> jacobian((a,x) -> a.^2 .* x, [1,2,3], 1)  # scalar argument has vector jacobian
([2 0 0; 0 4 0; 0 0 6], [1, 4, 9])

julia> jacobian((a,d) -> prod(a, dims=d), [1 2; 3 4; 5 6], 2)
([2 0 … 0 0; 0 4 … 3 0; 0 0 … 0 5], [0, 0, 0])
```

!!! warning
    For arguments of any type except `Number` & `AbstractArray`, the result is `nothing`.


```
julia> jacobian((a,s) -> a.^length(s), [1,2,3], "str")
([3 0 0; 0 12 0; 0 0 27], nothing)

julia> jacobian((a,t) -> sum(a .* t[1]) + t[2], [1,2,3], (4,5))
([4 4 4], nothing)

julia> gradient((a,t) -> sum(a .* t[1]) + t[2], [1,2,3], (4,5))  # gradient undersands the tuple
([4 4 4], (6, 1))
```
