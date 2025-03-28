```
Set{T} <: AbstractSet{T}
```

`Set`s sind veränderliche Container, die schnelle Mitgliedschaftstests ermöglichen.

`Set`s haben effiziente Implementierungen von Mengenoperationen wie `in`, `union` und `intersect`. Elemente in einem `Set` sind einzigartig, wie durch die Definition von `isequal` der Elemente bestimmt. Die Reihenfolge der Elemente in einem `Set` ist ein Implementierungsdetail und kann nicht darauf vertraut werden.

Siehe auch: [`AbstractSet`](@ref), [`BitSet`](@ref), [`Dict`](@ref), [`push!`](@ref), [`empty!`](@ref), [`union!`](@ref), [`in`](@ref), [`isequal`](@ref)

# Beispiele

```jldoctest; filter = r"^  '.'"ma
julia> s = Set("aaBca")
Set{Char} mit 3 Elementen:
  'a'
  'c'
  'B'

julia> push!(s, 'b')
Set{Char} mit 4 Elementen:
  'a'
  'b'
  'B'
  'c'

julia> s = Set([NaN, 0.0, 1.0, 2.0]);

julia> -0.0 in s # isequal(0.0, -0.0) ist falsch
falsch

julia> NaN in s # isequal(NaN, NaN) ist wahr
wahr
```
