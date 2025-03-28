```
foldl(op, itr; [init])
```

Wie [`reduce`](@ref), aber mit garantierter linker Assoziativität. Wenn angegeben, wird das Schlüsselwort-Argument `init` genau einmal verwendet. Im Allgemeinen ist es notwendig, `init` bereitzustellen, um mit leeren Sammlungen zu arbeiten.

Siehe auch [`mapfoldl`](@ref), [`foldr`](@ref), [`accumulate`](@ref).

# Beispiele

```jldoctest
julia> foldl(=>, 1:4)
((1 => 2) => 3) => 4

julia> foldl(=>, 1:4; init=0)
(((0 => 1) => 2) => 3) => 4

julia> accumulate(=>, (1,2,3,4))
(1, 1 => 2, (1 => 2) => 3, ((1 => 2) => 3) => 4)
```
