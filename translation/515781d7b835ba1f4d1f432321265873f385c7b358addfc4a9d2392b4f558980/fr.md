```
get(f::Union{Function, Type}, collection, key)
```

Retourne la valeur stockée pour la clé donnée, ou si aucune correspondance pour la clé n'est présente, retourne `f()`. Utilisez [`get!`](@ref) pour également stocker la valeur par défaut dans le dictionnaire.

Ceci est destiné à être appelé en utilisant la syntaxe de bloc `do`

```julia
get(dict, key) do
    # valeur par défaut calculée ici
    time()
end
```
