```
pop!(collection) -> item
```

Entfernt ein Element aus `collection` und gibt es zurück. Wenn `collection` ein geordnetes Container ist, wird das letzte Element zurückgegeben; für ungeordnete Container wird ein beliebiges Element zurückgegeben.

Siehe auch: [`popfirst!`](@ref), [`popat!`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref) und [`push!`](@ref).

# Beispiele

```jldoctest
julia> A=[1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> pop!(A)
3

julia> A
2-element Vector{Int64}:
 1
 2

julia> S = Set([1, 2])
Set{Int64} mit 2 Elementen:
  2
  1

julia> pop!(S)
2

julia> S
Set{Int64} mit 1 Element:
  1

julia> pop!(Dict(1=>2))
1 => 2
```
