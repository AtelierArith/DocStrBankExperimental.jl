```
showable(mime, x)
```

Renvoie une valeur booléenne indiquant si l'objet `x` peut être écrit sous le type `mime` donné.

(Par défaut, cela est déterminé automatiquement par l'existence de la méthode [`show`](@ref) correspondante pour `typeof(x)`. Certains types fournissent des méthodes `showable` personnalisées ; par exemple, si les formats MIME disponibles dépendent de la *valeur* de `x`.)

# Exemples

```jldoctest
julia> showable(MIME("text/plain"), rand(5))
true

julia> showable("image/png", rand(5))
false
```
