```
foldr(op, itr; [init])
```

Wie [`reduce`](@ref), aber mit garantierter rechter Assoziativität. Wenn das Schlüsselwort-Argument `init` bereitgestellt wird, wird es genau einmal verwendet. Im Allgemeinen ist es notwendig, `init` bereitzustellen, um mit leeren Sammlungen zu arbeiten.

# Beispiele

```jldoctest
julia> foldr(=>, 1:4)
1 => (2 => (3 => 4))

julia> foldr(=>, 1:4; init=0)
1 => (2 => (3 => (4 => 0)))
```
