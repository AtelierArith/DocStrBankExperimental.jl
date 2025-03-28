```
invoke(f, argtypes::Type, args...; kwargs...)
```

Invoquer une méthode pour la fonction générique donnée `f` correspondant aux types spécifiés `argtypes` sur les arguments spécifiés `args` et en passant les arguments de mot-clé `kwargs`. Les arguments `args` doivent être conformes aux types spécifiés dans `argtypes`, c'est-à-dire que la conversion n'est pas effectuée automatiquement. Cette méthode permet d'invoquer une méthode autre que la méthode la plus spécifique correspondante, ce qui est utile lorsque le comportement d'une définition plus générale est explicitement nécessaire (souvent dans le cadre de l'implémentation d'une méthode plus spécifique de la même fonction).

Soyez prudent lorsque vous utilisez `invoke` pour des fonctions que vous n'écrivez pas. Quelle définition est utilisée pour les `argtypes` donnés est un détail d'implémentation à moins que la fonction ne précise explicitement que l'appel avec certains `argtypes` fait partie de l'API publique. Par exemple, le changement entre `f1` et `f2` dans l'exemple ci-dessous est généralement considéré comme compatible car le changement est invisible pour l'appelant avec un appel normal (non-`invoke`). Cependant, le changement est visible si vous utilisez `invoke`.

# Exemples

```jldoctest
julia> f(x::Real) = x^2;

julia> f(x::Integer) = 1 + invoke(f, Tuple{Real}, x);

julia> f(2)
5

julia> f1(::Integer) = Integer
       f1(::Real) = Real;

julia> f2(x::Real) = _f2(x)
       _f2(::Integer) = Integer
       _f2(_) = Real;

julia> f1(1)
Integer

julia> f2(1)
Integer

julia> invoke(f1, Tuple{Real}, 1)
Real

julia> invoke(f2, Tuple{Real}, 1)
Integer
```
