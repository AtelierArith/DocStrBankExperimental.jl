```
Tuple{Types...}
```

Una tupla es un contenedor de longitud fija que puede contener cualquier valor de diferentes tipos, pero no se puede modificar (es inmutable). Los valores se pueden acceder mediante indexación. Los literales de tupla se escriben con comas y paréntesis:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"

julia> typeof(x)
Tuple{Float64, String, Int64}
```

Una tupla de longitud 1 debe escribirse con una coma, `(1,)`, ya que `(1)` sería solo un valor entre paréntesis. `()` representa la tupla vacía (de longitud 0).

Una tupla se puede construir a partir de un iterador utilizando un tipo `Tuple` como constructor:

```jldoctest
julia> Tuple(["a", 1])
("a", 1)

julia> Tuple{String, Float64}(["a", 1])
("a", 1.0)
```

Los tipos de tupla son covariantes en sus parámetros: `Tuple{Int}` es un subtipo de `Tuple{Any}`. Por lo tanto, `Tuple{Any}` se considera un tipo abstracto, y los tipos de tupla son concretos solo si sus parámetros lo son. Las tuplas no tienen nombres de campo; los campos solo se acceden por índice. Los tipos de tupla pueden tener cualquier número de parámetros.

Consulta la sección del manual sobre [Tipos de Tupla](@ref).

Consulta también [`Vararg`](@ref), [`NTuple`](@ref), [`ntuple`](@ref), [`tuple`](@ref), [`NamedTuple`](@ref).
