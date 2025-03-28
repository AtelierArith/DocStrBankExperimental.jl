```
instances(T::Type)
```

Gibt eine Sammlung aller Instanzen des angegebenen Typs zurück, falls zutreffend. Wird hauptsächlich für enumerierte Typen verwendet (siehe `@enum`).

# Beispiele

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
