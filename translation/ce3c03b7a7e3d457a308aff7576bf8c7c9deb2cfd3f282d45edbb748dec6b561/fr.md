```
@boundscheck(blk)
```

Annotates the expression `blk` as a bounds checking block, allowing it to be elided by [`@inbounds`](@ref).

!!! note
    La fonction dans laquelle `@boundscheck` est écrite doit être intégrée dans son appelant pour que `@inbounds` ait un effet.


# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> @inline function g(A, i)
           @boundscheck checkbounds(A, i)
           return "accès à ($A)[$i]"
       end;

julia> f1() = return g(1:2, -1);

julia> f2() = @inbounds return g(1:2, -1);

julia> f1()
ERROR: BoundsError: tentative d'accès à un UnitRange{Int64} de 2 éléments à l'index [-1]
Stacktrace:
 [1] throw_boundserror(::UnitRange{Int64}, ::Tuple{Int64}) at ./abstractarray.jl:455
 [2] checkbounds at ./abstractarray.jl:420 [inlined]
 [3] g at ./none:2 [inlined]
 [4] f1() at ./none:1
 [5] top-level scope

julia> f2()
"accès à (1:2)[-1]"
```

!!! warning
    L'annotation `@boundscheck` vous permet, en tant qu'auteur de bibliothèque, de choisir de permettre à *d'autres codes* de supprimer vos vérifications de limites avec [`@inbounds`](@ref). Comme noté là-bas, l'appelant doit vérifier—en utilisant des informations auxquelles il peut accéder—que ses accès sont valides avant d'utiliser `@inbounds`. Par exemple, pour l'indexation dans vos sous-classes [`AbstractArray`](@ref), cela implique de vérifier les indices par rapport à ses [`axes`](@ref). Par conséquent, les annotations `@boundscheck` ne doivent être ajoutées à une implémentation de [`getindex`](@ref) ou [`setindex!`](@ref) qu'après vous être assuré que son comportement est correct.

