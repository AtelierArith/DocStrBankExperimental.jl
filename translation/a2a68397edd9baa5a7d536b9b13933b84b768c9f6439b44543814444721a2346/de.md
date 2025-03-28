```
getkey(collection, key, default)
```

Gibt den Schlüssel zurück, der dem Argument `key` entspricht, wenn er in `collection` vorhanden ist, andernfalls wird `default` zurückgegeben.

# Beispiele

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} mit 2 Einträgen:
  'a' => 2
  'b' => 3

julia> getkey(D, 'a', 1)
'a': ASCII/Unicode U+0061 (Kategorie Ll: Buchstabe, Kleinbuchstabe)

julia> getkey(D, 'd', 'a')
'a': ASCII/Unicode U+0061 (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```
