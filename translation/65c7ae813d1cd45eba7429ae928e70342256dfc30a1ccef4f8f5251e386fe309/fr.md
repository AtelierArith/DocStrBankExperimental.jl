```
@ncallkw N f kw sym...
```

Générez une expression d'appel de fonction avec des arguments de mot-clé `kw...`. Comme dans le cas de [`@ncall`](@ref), `sym` représente un nombre quelconque d'arguments de fonction, dont le dernier peut être une expression de fonction anonyme et est développé en `N` arguments.

# Exemples

```jldoctest
julia> using Base.Cartesian

julia> f(x...; a, b = 1, c = 2, d = 3) = +(x..., a, b, c, d);

julia> x_1, x_2 = (-1, -2); b = 0; kw = (c = 0, d = 0);

julia> @ncallkw 2 f (; a = 0, b, kw...) x
-3

```
