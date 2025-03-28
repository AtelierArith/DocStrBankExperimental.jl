```
findall(f::Function, A)
```

Gibt einen Vektor `I` der Indizes oder Schlüssel von `A` zurück, wo `f(A[I])` `true` zurückgibt. Wenn es keine solchen Elemente von `A` gibt, wird ein leeres Array zurückgegeben.

Indizes oder Schlüssel sind vom gleichen Typ wie die, die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegeben werden.

# Beispiele

```jldoctest
julia> x = [1, 3, 4]
3-element Vector{Int64}:
 1
 3
 4

julia> findall(isodd, x)
2-element Vector{Int64}:
 1
 2

julia> A = [1 2 0; 3 4 0]
2×3 Matrix{Int64}:
 1  2  0
 3  4  0
julia> findall(isodd, A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 1)

julia> findall(!iszero, A)
4-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 1)
 CartesianIndex(1, 2)
 CartesianIndex(2, 2)

julia> d = Dict(:A => 10, :B => -1, :C => 0)
Dict{Symbol, Int64} mit 3 Einträgen:
  :A => 10
  :B => -1
  :C => 0

julia> findall(x -> x >= 0, d)
2-element Vector{Symbol}:
 :A
 :C

```
