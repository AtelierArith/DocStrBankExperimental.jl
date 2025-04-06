```
pares(colección)
```

Devuelve un iterador sobre pares `clave => valor` para cualquier colección que mapea un conjunto de claves a un conjunto de valores. Esto incluye arreglos, donde las claves son los índices del arreglo. Cuando las entradas se almacenan internamente en una tabla hash, como es el caso de `Dict`, el orden en que se devuelven puede variar. Pero `keys(a)`, `values(a)` y `pairs(a)` iteran sobre `a` y devuelven los elementos en el mismo orden.

# Ejemplos

```jldoctest
julia> a = Dict(zip(["a", "b", "c"], [1, 2, 3]))
Dict{String, Int64} con 3 entradas:
  "c" => 3
  "b" => 2
  "a" => 1

julia> pairs(a)
Dict{String, Int64} con 3 entradas:
  "c" => 3
  "b" => 2
  "a" => 1

julia> foreach(println, pairs(["a", "b", "c"]))
1 => "a"
2 => "b"
3 => "c"

julia> (;a=1, b=2, c=3) |> pairs |> collect
Vector{Pair{Symbol, Int64}} de 3 elementos:
 :a => 1
 :b => 2
 :c => 3

julia> (;a=1, b=2, c=3) |> collect
Vector{Int64} de 3 elementos:
 1
 2
 3
```
