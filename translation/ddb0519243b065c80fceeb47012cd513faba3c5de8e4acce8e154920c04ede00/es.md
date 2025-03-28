```
global
```

`global x` hace que `x` en el ámbito actual y sus ámbitos internos se refiera a la variable global de ese nombre. Consulta la [sección del manual sobre el alcance de las variables](@ref scope-of-variables) para más información.

# Ejemplos

```jldoctest
julia> z = 3
3

julia> function foo()
           global z = 6 # usa la variable z definida fuera de foo
       end
foo (función genérica con 1 método)

julia> foo()
6

julia> z
6
```
