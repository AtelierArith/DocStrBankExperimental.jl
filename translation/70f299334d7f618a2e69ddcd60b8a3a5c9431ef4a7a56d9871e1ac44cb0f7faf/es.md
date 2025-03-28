```
Union{Tipos...}
```

Un tipo `Union` es un tipo abstracto que incluye todas las instancias de cualquiera de sus tipos de argumento. Esto significa que `T <: Union{T,S}` y `S <: Union{T,S}`.

Al igual que otros tipos abstractos, no se puede instanciar, incluso si todos sus argumentos no son abstractos.

# Ejemplos

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString # instancia de Int está incluida en la unión
true

julia> "¡Hola!" isa IntOrString # String también está incluido
true

julia> 1.0 isa IntOrString # Float64 no está incluido porque no es ni Int ni AbstractString
false
```

# Ayuda Extendida

A diferencia de la mayoría de los otros tipos paramétricos, las uniones son covariantes en sus parámetros. Por ejemplo, `Union{Real, String}` es un subtipo de `Union{Number, AbstractString}`.

La unión vacía [`Union{}`](@ref) es el tipo inferior de Julia.
