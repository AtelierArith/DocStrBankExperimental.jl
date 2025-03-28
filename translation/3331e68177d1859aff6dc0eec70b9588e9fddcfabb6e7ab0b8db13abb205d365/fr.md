```
displaysize([io::IO]) -> (lignes, colonnes)
```

Retourne la taille nominale de l'écran qui peut être utilisée pour le rendu de la sortie vers cet objet `IO`. Si aucun input n'est fourni, les variables d'environnement `LINES` et `COLUMNS` sont lues. Si celles-ci ne sont pas définies, une taille par défaut de `(24, 80)` est retournée.

# Exemples

```jldoctest
julia> withenv("LINES" => 30, "COLUMNS" => 100) do
           displaysize()
       end
(30, 100)
```

Pour obtenir la taille de votre TTY,

```julia-repl
julia> displaysize(stdout)
(34, 147)
```
