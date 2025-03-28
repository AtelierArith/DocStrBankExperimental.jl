```
abspath(path::AbstractString) -> String
```

Convertit un chemin en un chemin absolu en ajoutant le répertoire actuel si nécessaire. Normalise également le chemin comme dans [`normpath`](@ref).

# Exemples

Si vous êtes dans un répertoire appelé `JuliaExample` et que les données que vous utilisez se trouvent deux niveaux au-dessus par rapport au répertoire `JuliaExample`, vous pourriez écrire :

```
abspath("../../data")
```

Ce qui donne un chemin comme `"/home/JuliaUser/data/"`.

Voir aussi [`joinpath`](@ref), [`pwd`](@ref), [`expanduser`](@ref).
