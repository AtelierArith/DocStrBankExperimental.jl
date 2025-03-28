```
show([io::IO = stdout], x)
```

Écrit une représentation textuelle d'une valeur `x` dans le flux de sortie `io`. Les nouveaux types `T` devraient surcharger `show(io::IO, x::T)`. La représentation utilisée par `show` inclut généralement un formatage spécifique à Julia et des informations de type, et devrait être analysable en code Julia lorsque cela est possible.

[`repr`](@ref) renvoie la sortie de `show` sous forme de chaîne.

Pour une sortie textuelle plus détaillée et lisible par l'homme pour les objets de type `T`, définissez également `show(io::IO, ::MIME"text/plain", ::T)`. Il est recommandé de vérifier la clé `:compact` de [`IOContext`](@ref) (souvent vérifiée comme `get(io, :compact, false)::Bool`) de `io` dans de telles méthodes, car certains conteneurs affichent leurs éléments en appelant cette méthode avec `:compact => true`.

Voir aussi [`print`](@ref), qui écrit des représentations non décorées.

# Exemples

```jldoctest
julia> show("Hello World!")
"Hello World!"
julia> print("Hello World!")
Hello World!
```
