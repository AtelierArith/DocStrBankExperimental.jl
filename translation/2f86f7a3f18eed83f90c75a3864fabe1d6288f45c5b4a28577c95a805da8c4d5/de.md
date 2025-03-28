```
ntuple(f, ::Val{N})
```

Erstellt ein Tupel der Länge `N`, wobei jedes Element als `f(i)` berechnet wird, wobei `i` der Index des Elements ist. Durch die Verwendung eines `Val(N)`-Arguments ist es möglich, dass diese Version von ntuple effizienteren Code generieren kann als die Version, die die Länge als Ganzzahl verwendet. Aber `ntuple(f, N)` ist vorzuziehen gegenüber `ntuple(f, Val(N))` in Fällen, in denen `N` zur Compile-Zeit nicht bestimmt werden kann.

# Beispiele

```jldoctest
julia> ntuple(i -> 2*i, Val(4))
(2, 4, 6, 8)
```
