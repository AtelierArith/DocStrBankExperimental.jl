```
@isdefined s -> Bool
```

Prueba si la variable `s` está definida en el ámbito actual.

Consulta también [`isdefined`](@ref) para propiedades de campo y [`isassigned`](@ref) para índices de matriz o [`haskey`](@ref) para otros mapeos.

# Ejemplos

```jldoctest
julia> @isdefined newvar
false

julia> newvar = 1
1

julia> @isdefined newvar
true

julia> function f()
           println(@isdefined x)
           x = 3
           println(@isdefined x)
       end
f (generic function with 1 method)

julia> f()
false
true
```
