```
VersionNumber
```

Type de numéro de version qui suit les spécifications de [versionnement sémantique (semver)](https://semver.org/), composé de valeurs numériques majeures, mineures et de correctifs, suivies d'annotations alphanumériques de pré-version et de construction.

Les objets `VersionNumber` peuvent être comparés avec tous les opérateurs de comparaison standard (`==`, `<`, `<=`, etc.), le résultat suivant les règles de semver.

`VersionNumber` a les champs publics suivants :

  * `v.major::Integer`
  * `v.minor::Integer`
  * `v.patch::Integer`
  * `v.prerelease::Tuple{Vararg{Union{Integer, AbstractString}}}`
  * `v.build::Tuple{Vararg{Union{Integer, AbstractString}}}`

Voir aussi [`@v_str`](@ref) pour construire efficacement des objets `VersionNumber` à partir de chaînes littérales au format semver, [`VERSION`](@ref) pour le `VersionNumber` de Julia lui-même, et [Littéraux de Numéro de Version](@ref man-version-number-literals) dans le manuel.

# Exemples

```jldoctest
julia> a = VersionNumber(1, 2, 3)
v"1.2.3"

julia> a >= v"1.2"
true

julia> b = VersionNumber("2.0.1-rc1")
v"2.0.1-rc1"

julia> b >= v"2.0.1"
false
```
