```
reshape(A, dims...) -> AbstractArray
reshape(A, dims) -> AbstractArray
```

Devuelve un array con los mismos datos que `A`, pero con diferentes tamaños de dimensión o número de dimensiones. Los dos arrays comparten los mismos datos subyacentes, de modo que el resultado es mutable si y solo si `A` es mutable, y establecer elementos de uno altera los valores del otro.

Las nuevas dimensiones pueden especificarse ya sea como una lista de argumentos o como una tupla de forma. Como máximo, se puede especificar una dimensión con un `:`, en cuyo caso su longitud se calcula de tal manera que su producto con todas las dimensiones especificadas sea igual a la longitud del array original `A`. El número total de elementos no debe cambiar.

# Ejemplos

```jldoctest
julia> A = Vector(1:16)
16-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16

julia> reshape(A, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reshape(A, 2, :)
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> reshape(1:6, 2, 3)
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6
```
