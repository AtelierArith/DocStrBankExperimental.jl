```
applicable(f, args...) -> Bool
```

Determina si la función genérica dada tiene un método aplicable a los argumentos dados.

Ver también [`hasmethod`](@ref).

# Ejemplos

```jldoctest
julia> function f(x, y)
           x + y
       end;

julia> applicable(f, 1)
false

julia> applicable(f, 1, 2)
true
```
