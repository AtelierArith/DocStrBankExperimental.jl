```
continue
```

Saltar la iteración actual del bucle.

# Ejemplos

```jldoctest
julia> for i = 1:6
           iseven(i) && continue
           println(i)
       end
1
3
5
```
