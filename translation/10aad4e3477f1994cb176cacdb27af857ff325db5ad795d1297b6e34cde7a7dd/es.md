```
algo(x...)
```

Devuelve el primer valor en los argumentos que no sea igual a [`nothing`](@ref), si lo hay. De lo contrario, lanza un error. Los argumentos de tipo [`Some`](@ref) se desenvuelven.

Véase también [`coalesce`](@ref), [`skipmissing`](@ref), [`@something`](@ref).

# Ejemplos

```jldoctest
julia> algo(nothing, 1)
1

julia> algo(Some(1), nothing)
1

julia> algo(Some(nothing), 2) === nothing
true

julia> algo(missing, nothing)
missing

julia> algo(nothing, nothing)
ERROR: ArgumentError: No hay argumentos de valor presentes
```
