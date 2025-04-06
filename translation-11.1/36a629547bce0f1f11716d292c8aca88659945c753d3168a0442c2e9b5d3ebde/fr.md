```
print([io::IO], xs...)
```

Écrit dans `io` (ou dans le flux de sortie par défaut [`stdout`](@ref) si `io` n'est pas donné) une représentation textuelle canonique (non décorée). La représentation utilisée par `print` inclut un formatage minimal et essaie d'éviter les détails spécifiques à Julia.

`print` se rabat sur l'appel de `show`, donc la plupart des types devraient simplement définir `show`. Définissez `print` si votre type a une représentation "plain" séparée. Par exemple, `show` affiche les chaînes avec des guillemets, et `print` affiche les chaînes sans guillemets.

Voir aussi [`println`](@ref), [`string`](@ref), [`printstyled`](@ref).

# Exemples

```jldoctest
julia> print("Hello World!")
Hello World!
julia> io = IOBuffer();

julia> print(io, "Hello", ' ', :World!)

julia> String(take!(io))
"Hello World!"
```
