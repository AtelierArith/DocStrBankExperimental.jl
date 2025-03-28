```
fill!(A, x)
```

Rellena el arreglo `A` con el valor `x`. Si `x` es una referencia de objeto, todos los elementos harán referencia al mismo objeto. `fill!(A, Foo())` devolverá `A` lleno con el resultado de evaluar `Foo()` una vez.

# Ejemplos

```jldoctest
julia> A = zeros(2,3)
2×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2.)
2×3 Matrix{Float64}:
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> a = [1, 1, 1]; A = fill!(Vector{Vector{Int}}(undef, 3), a); a[1] = 2; A
3-element Vector{Vector{Int64}}:
 [2, 1, 1]
 [2, 1, 1]
 [2, 1, 1]

julia> x = 0; f() = (global x += 1; x); fill!(Vector{Int}(undef, 3), f())
3-element Vector{Int64}:
 1
 1
 1
```
