```
isdefined(m::Module, s::Symbol, [order::Symbol])
isdefined(object, s::Symbol, [order::Symbol])
isdefined(object, index::Int, [order::Symbol])
```

Teste si une variable globale ou un champ d'objet est défini. Les arguments peuvent être un module et un symbole ou un objet composite et un nom de champ (sous forme de symbole) ou un index. En option, un ordre peut être défini pour l'opération. Si le champ a été déclaré `@atomic`, il est fortement recommandé que la spécification soit compatible avec les stockages à cet emplacement. Sinon, s'il n'est pas déclaré comme `@atomic`, ce paramètre doit être `:not_atomic` s'il est spécifié.

Pour tester si un élément de tableau est défini, utilisez [`isassigned`](@ref) à la place.

Voir aussi [`@isdefined`](@ref).

# Exemples

```jldoctest
julia> isdefined(Base, :sum)
true

julia> isdefined(Base, :NonExistentMethod)
false

julia> a = 1//2;

julia> isdefined(a, 2)
true

julia> isdefined(a, 3)
false

julia> isdefined(a, :num)
true

julia> isdefined(a, :numerator)
false
```
