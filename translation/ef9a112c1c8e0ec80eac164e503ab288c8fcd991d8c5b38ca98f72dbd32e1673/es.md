```
\(x, y)
```

Operador de división izquierda: multiplicación de `y` por la inversa de `x` a la izquierda. Devuelve resultados de punto flotante para argumentos enteros.

# Ejemplos

```jldoctest
julia> 3 \ 6
2.0

julia> inv(3) * 6
2.0

julia> A = [4 3; 2 1]; x = [5, 6];

julia> A \ x
2-element Vector{Float64}:
  6.5
 -7.0

julia> inv(A) * x
2-element Vector{Float64}:
  6.5
 -7.0
```
