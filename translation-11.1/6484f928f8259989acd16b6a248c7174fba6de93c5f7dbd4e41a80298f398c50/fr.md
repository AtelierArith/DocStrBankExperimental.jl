```
sizeof(T::DataType)
sizeof(obj)
```

Taille, en octets, de la représentation binaire canonique du `DataType` donné `T`, le cas échéant. Ou la taille, en octets, de l'objet `obj` s'il n'est pas un `DataType`.

Voir aussi [`Base.summarysize`](@ref).

# Exemples

```jldoctest
julia> sizeof(Float32)
4

julia> sizeof(ComplexF64)
16

julia> sizeof(1.0)
8

julia> sizeof(collect(1.0:10.0))
80

julia> struct StructWithPadding
           x::Int64
           flag::Bool
       end

julia> sizeof(StructWithPadding) # pas la somme de `sizeof` des champs en raison du remplissage
16

julia> sizeof(Int64) + sizeof(Bool) # différent de ci-dessus
9
```

Si le `DataType` `T` n'a pas de taille spécifique, une erreur est levée.

```jldoctest
julia> sizeof(AbstractArray)
ERROR: Le type abstrait AbstractArray n'a pas de taille définie.
Stacktrace:
[...]
```
