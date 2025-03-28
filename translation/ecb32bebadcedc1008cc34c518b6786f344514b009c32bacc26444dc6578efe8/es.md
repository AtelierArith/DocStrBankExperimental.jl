```
cmp(x,y)
```

Devuelve -1, 0 o 1 dependiendo de si `x` es menor que, igual a, o mayor que `y`, respectivamente. Utiliza el orden total implementado por `isless`.

# Ejemplos

```jldoctest
julia> cmp(1, 2)
-1

julia> cmp(2, 1)
1

julia> cmp(2+im, 3-im)
ERROR: MethodError: no method matching isless(::Complex{Int64}, ::Complex{Int64})
[...]
```
