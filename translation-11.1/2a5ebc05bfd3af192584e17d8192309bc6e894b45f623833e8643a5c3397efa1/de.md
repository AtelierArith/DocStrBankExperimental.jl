```
mod(x, y)
rem(x, y, RoundDown)
```

Die Reduktion von `x` modulo `y`, oder äquivalent, der Rest von `x` nach ganzzahliger Division durch `y`, d.h. `x - y*fld(x,y)`, wenn ohne Zwischenrundung berechnet.

Das Ergebnis hat das gleiche Vorzeichen wie `y` und eine Größe, die kleiner ist als `abs(y)` (mit einigen Ausnahmen, siehe Hinweis unten).

!!! Hinweis     Wenn mit Fließkommawerten verwendet, kann das exakte Ergebnis möglicherweise nicht durch den Typ dargestellt werden, und es kann daher zu Rundungsfehlern kommen. Insbesondere, wenn das exakte Ergebnis sehr nahe an `y` liegt, kann es auf `y` gerundet werden.

Siehe auch: [`rem`](@ref), [`div`](@ref), [`fld`](@ref), [`mod1`](@ref), [`invmod`](@ref).

```jldoctest
julia> mod(8, 3)
2

julia> mod(9, 3)
0

julia> mod(8.9, 3)
2.9000000000000004

julia> mod(eps(), 3)
2.220446049250313e-16

julia> mod(-eps(), 3)
3.0

julia> mod.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) mit eltype Int64:
 1  2  0  1  2  0  1  2  0  1  2
```
