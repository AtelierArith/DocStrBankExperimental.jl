```
ComposedFunction{Outer,Inner} <: Function
```

Représente la composition de deux objets appelables `outer::Outer` et `inner::Inner`. C'est-à-dire

```julia
ComposedFunction(outer, inner)(args...; kw...) === outer(inner(args...; kw...))
```

La manière préférée de construire une instance de `ComposedFunction` est d'utiliser l'opérateur de composition [`∘`](@ref) :

```jldoctest
julia> sin ∘ cos === ComposedFunction(sin, cos)
true

julia> typeof(sin∘cos)
ComposedFunction{typeof(sin), typeof(cos)}
```

Les pièces composées sont stockées dans les champs de `ComposedFunction` et peuvent être récupérées comme suit :

```jldoctest
julia> composition = sin ∘ cos
sin ∘ cos

julia> composition.outer === sin
true

julia> composition.inner === cos
true
```

!!! compat "Julia 1.6"
    ComposedFunction nécessite au moins Julia 1.6. Dans les versions antérieures, `∘` renvoie une fonction anonyme à la place.


Voir aussi [`∘`](@ref).
