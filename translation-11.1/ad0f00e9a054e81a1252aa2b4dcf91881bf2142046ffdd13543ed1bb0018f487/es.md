```
isdiag(A) -> Bool
```

Prueba si una matriz es diagonal en el sentido de que `iszero(A[i,j])` es verdadero a menos que `i == j`. Ten en cuenta que no es necesario que `A` sea cuadrada; si también deseas verificar eso, necesitas comprobar que `size(A, 1) == size(A, 2)`.

# Ejemplos

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> isdiag(a)
false

julia> b = [im 0; 0 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  0+0im
 0+0im  0-1im

julia> isdiag(b)
true

julia> c = [1 0 0; 0 2 0]
2×3 Matrix{Int64}:
 1  0  0
 0  2  0

julia> isdiag(c)
true

julia> d = [1 0 0; 0 2 3]
2×3 Matrix{Int64}:
 1  0  0
 0  2  3

julia> isdiag(d)
false
```
