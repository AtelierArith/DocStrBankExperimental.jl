```
join([io::IO,] iterator [, delim [, last]])
```

Joindre tout `iterator` en une seule chaîne, en insérant le délimiteur donné (le cas échéant) entre les éléments adjacents. Si `last` est donné, il sera utilisé à la place de `delim` entre les deux derniers éléments. Chaque élément de `iterator` est converti en chaîne via `print(io::IOBuffer, x)`. Si `io` est donné, le résultat est écrit dans `io` plutôt que retourné en tant que `String`.

# Exemples

```jldoctest
julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"

julia> join([1,2,3,4,5])
"12345"
```
