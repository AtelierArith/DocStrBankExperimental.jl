```
instances(T::Type)
```

Renvoie une collection de toutes les instances du type donné, si applicable. Principalement utilisé pour les types énumérés (voir `@enum`).

# Exemples

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
