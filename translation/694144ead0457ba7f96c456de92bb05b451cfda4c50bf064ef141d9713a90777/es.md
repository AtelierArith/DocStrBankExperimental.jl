```
pairs(IndexLinear(), A)
pairs(IndexCartesian(), A)
pairs(IndexStyle(A), A)
```

Un iterador que accede a cada elemento del arreglo `A`, devolviendo `i => x`, donde `i` es el índice del elemento y `x = A[i]`. Idéntico a `pairs(A)`, excepto que se puede seleccionar el estilo del índice. También es similar a `enumerate(A)`, excepto que `i` será un índice válido para `A`, mientras que `enumerate` siempre cuenta desde 1 independientemente de los índices de `A`.

Especificar [`IndexLinear()`](@ref) asegura que `i` será un entero; especificar [`IndexCartesian()`](@ref) asegura que `i` será un [`Base.CartesianIndex`](@ref); especificar `IndexStyle(A)` elige el que se ha definido como el estilo de indexación nativo para el arreglo `A`.

La mutación de los límites del arreglo subyacente invalidará este iterador.

# Ejemplos

```jldoctest
julia> A = ["a" "d"; "b" "e"; "c" "f"];

julia> for (index, value) in pairs(IndexStyle(A), A)
           println("$index $value")
       end
1 a
2 b
3 c
4 d
5 e
6 f

julia> S = view(A, 1:2, :);

julia> for (index, value) in pairs(IndexStyle(S), S)
           println("$index $value")
       end
CartesianIndex(1, 1) a
CartesianIndex(2, 1) b
CartesianIndex(1, 2) d
CartesianIndex(2, 2) e
```

Ver también [`IndexStyle`](@ref), [`axes`](@ref).
