```
lazy"str"
```

Créez un [`LazyString`](@ref) en utilisant la syntaxe d'interpolation de chaîne régulière. Notez que les interpolations sont *évaluées* au moment de la construction de LazyString, mais que *l'impression* est retardée jusqu'au premier accès à la chaîne.

Consultez la documentation de [`LazyString`](@ref) pour les propriétés de sécurité des programmes concurrents.

# Exemples

```
julia> n = 5; str = lazy"n is $n"
"n is 5"

julia> typeof(str)
LazyString
```

!!! compat "Julia 1.8"
    `lazy"str"` nécessite Julia 1.8 ou une version ultérieure.

