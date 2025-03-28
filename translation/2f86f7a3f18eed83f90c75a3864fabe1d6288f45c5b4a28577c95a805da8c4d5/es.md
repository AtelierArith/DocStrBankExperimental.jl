```
ntuple(f, ::Val{N})
```

Crea una tupla de longitud `N`, calculando cada elemento como `f(i)`, donde `i` es el índice del elemento. Al tomar un argumento `Val(N)`, es posible que esta versión de ntuple genere un código más eficiente que la versión que toma la longitud como un entero. Pero `ntuple(f, N)` es preferible a `ntuple(f, Val(N))` en casos donde `N` no se puede determinar en tiempo de compilación.

# Ejemplos

```jldoctest
julia> ntuple(i -> 2*i, Val(4))
(2, 4, 6, 8)
```
