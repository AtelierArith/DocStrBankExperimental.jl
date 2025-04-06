```
Union{Types...}
```

Un type `Union` est un type abstrait qui inclut toutes les instances de n'importe lequel de ses types d'argument. Cela signifie que `T <: Union{T,S}` et `S <: Union{T,S}`.

Comme d'autres types abstraits, il ne peut pas être instancié, même si tous ses arguments ne sont pas abstraits.

# Exemples

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString # une instance d'Int est incluse dans l'union
true

julia> "Hello!" isa IntOrString # String est également inclus
true

julia> 1.0 isa IntOrString # Float64 n'est pas inclus car il n'est ni Int ni AbstractString
false
```

# Aide Étendue

Contrairement à la plupart des autres types paramétriques, les unions sont covariantes dans leurs paramètres. Par exemple, `Union{Real, String}` est un sous-type de `Union{Number, AbstractString}`.

L'union vide [`Union{}`](@ref) est le type le plus bas de Julia.
