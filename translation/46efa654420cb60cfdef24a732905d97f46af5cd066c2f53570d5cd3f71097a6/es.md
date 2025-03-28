```
splat(f)
```

Equivalente a

```julia
    my_splat(f) = args->f(args...)
```

es decir, dado una función, devuelve una nueva función que toma un argumento y lo expande en la función original. Esto es útil como un adaptador para pasar una función de múltiples argumentos en un contexto que espera un solo argumento, pero pasa una tupla como ese único argumento.

# Ejemplos

```jldoctest
julia> map(splat(+), zip(1:3,4:6))
3-element Vector{Int64}:
 5
 7
 9

julia> my_add = splat(+)
splat(+)

julia> my_add((1,2,3))
6
```
