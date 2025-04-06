```
local
```

`local` introduce una nueva variable local. Consulta la [sección del manual sobre el alcance de las variables](@ref scope-of-variables) para más información.

# Ejemplos

```jldoctest
julia> function foo(n)
           x = 0
           for i = 1:n
               local x # introduce un x local al bucle
               x = i
           end
           x
       end
foo (función genérica con 1 método)

julia> foo(10)
0
```
