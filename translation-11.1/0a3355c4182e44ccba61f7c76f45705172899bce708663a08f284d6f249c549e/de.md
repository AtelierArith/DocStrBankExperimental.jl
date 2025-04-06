```
zip(iters...)
```

Führen Sie mehrere Iteratoren gleichzeitig aus, bis einer von ihnen erschöpft ist. Der Werttyp des `zip`-Iterators ist ein Tupel von Werten seiner Unteriteratoren.

!!! note
    `zip` ordnet die Aufrufe seiner Unteriteratoren so, dass zustandsbehaftete Iteratoren nicht vorankommen, wenn ein anderer Iterator in der aktuellen Iteration endet.


!!! note
    `zip()` ohne Argumente ergibt einen unendlichen Iterator leerer Tupel.


Siehe auch: [`enumerate`](@ref), [`Base.splat`](@ref).

# Beispiele

```jldoctest
julia> a = 1:5
1:5

julia> b = ["e","d","b","c","a"]
5-element Vector{String}:
 "e"
 "d"
 "b"
 "c"
 "a"

julia> c = zip(a,b)
zip(1:5, ["e", "d", "b", "c", "a"])

julia> length(c)
5

julia> first(c)
(1, "e")
```
