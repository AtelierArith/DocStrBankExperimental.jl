```
|>(x, f)
```

Operador infijo que aplica la función `f` al argumento `x`. Esto permite que `f(g(x))` se escriba como `x |> g |> f`. Cuando se usa con funciones anónimas, generalmente se requieren paréntesis alrededor de la definición para obtener la cadena deseada.

# Ejemplos

```jldoctest
julia> 4 |> inv
0.25

julia> [2, 3, 5] |> sum |> inv
0.1

julia> [0 1; 2 3] .|> (x -> x^2) |> sum
14
```
