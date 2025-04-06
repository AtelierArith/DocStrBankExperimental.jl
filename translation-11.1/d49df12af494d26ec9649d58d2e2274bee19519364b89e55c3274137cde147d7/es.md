```
countfrom(start=1, step=1)
```

Un iterador que cuenta para siempre, comenzando en `start` e incrementando por `step`.

# Ejemplos

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
