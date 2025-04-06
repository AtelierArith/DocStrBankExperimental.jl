```
kron(A, B)
```

Calcula el producto de Kronecker de dos vectores, matrices o números.

Para vectores reales `v` y `w`, el producto de Kronecker está relacionado con el producto exterior por `kron(v,w) == vec(w * transpose(v))` o `w * transpose(v) == reshape(kron(v,w), (length(w), length(v)))`. Nota cómo el orden de `v` y `w` difiere a la izquierda y a la derecha de estas expresiones (debido al almacenamiento por columnas). Para vectores complejos, el producto exterior `w * v'` también difiere por la conjugación de `v`.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> B = [im 1; 1 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  1+0im
 1+0im  0-1im

julia> kron(A, B)
4×4 Matrix{Complex{Int64}}:
 0+1im  1+0im  0+2im  2+0im
 1+0im  0-1im  2+0im  0-2im
 0+3im  3+0im  0+4im  4+0im
 3+0im  0-3im  4+0im  0-4im

julia> v = [1, 2]; w = [3, 4, 5];

julia> w*transpose(v)
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10

julia> reshape(kron(v,w), (length(w), length(v)))
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10
```
