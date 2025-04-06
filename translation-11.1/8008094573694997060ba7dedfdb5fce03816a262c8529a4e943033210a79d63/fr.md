```
@deprecate old new [export_old=true]
```

Déprécier la méthode `old` et spécifier l'appel de remplacement `new`, en définissant une nouvelle méthode `old` avec la signature spécifiée dans le processus.

Pour empêcher `old` d'être exporté, définissez `export_old` sur `false`.

Voir aussi [`Base.depwarn()`](@ref).

!!! compat "Julia 1.5"
    À partir de Julia 1.5, les fonctions définies par `@deprecate` ne génèrent pas d'avertissement lorsque `julia` est exécuté sans le drapeau `--depwarn=yes` activé, car la valeur par défaut de l'option `--depwarn` est `no`. Les avertissements sont imprimés lors des tests exécutés par `Pkg.test()`.


# Exemples

```jldoctest
julia> @deprecate old(x) new(x)
old (generic function with 1 method)

julia> @deprecate old(x) new(x) false
old (generic function with 1 method)
```

Les appels à `@deprecate` sans annotations de type explicites définiront des méthodes dépréciées acceptant n'importe quel nombre d'arguments positionnels et d'arguments de mot-clé de type `Any`.

!!! compat "Julia 1.9"
    Les arguments de mot-clé sont transmis lorsqu'il n'y a pas d'annotation de type explicite à partir de Julia 1.9. Pour les versions antérieures, vous pouvez transmettre manuellement les arguments positionnels et de mot-clé en faisant `@deprecate old(args...; kwargs...) new(args...; kwargs...)`.


Pour restreindre la dépréciation à une signature spécifique, annotez les arguments de `old`. Par exemple,

```jldoctest; filter = r"@ .*"a
julia> new(x::Int) = x;

julia> new(x::Float64) = 2x;

julia> @deprecate old(x::Int) new(x);

julia> methods(old)
# 1 method for generic function "old" from Main:
 [1] old(x::Int64)
     @ deprecated.jl:94
```

définira et dépréciera une méthode `old(x::Int)` qui reflète `new(x::Int)` mais ne définira ni ne dépréciera la méthode `old(x::Float64)`.
