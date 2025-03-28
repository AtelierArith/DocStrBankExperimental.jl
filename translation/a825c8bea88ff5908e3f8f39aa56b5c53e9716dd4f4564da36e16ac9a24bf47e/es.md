```
for
```

Los bucles `for` evalúan repetidamente un bloque de declaraciones mientras iteran sobre una secuencia de valores.

La variable de iteración siempre es una nueva variable, incluso si existe una variable con el mismo nombre en el ámbito que la rodea. Usa [`outer`](@ref) para reutilizar una variable local existente para la iteración.

# Ejemplos

```jldoctest
julia> for i in [1, 4, 0]
           println(i)
       end
1
4
0
```
