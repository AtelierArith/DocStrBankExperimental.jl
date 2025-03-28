```
for outer
```

Reutiliza una variable local existente para la iteración en un bucle `for`.

Consulta la [sección del manual sobre el alcance de las variables](@ref scope-of-variables) para más información.

Consulta también [`for`](@ref).

# Ejemplos

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # vacío
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # vacío
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # variable global
       for outer i = 1:3
       end
ERROR: syntax: no outer local variable declaration exists for "for outer"
[...]
```
