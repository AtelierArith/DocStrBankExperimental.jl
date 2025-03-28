```
end
```

`end` markiert den Abschluss eines Blocks von Ausdrücken, zum Beispiel [`module`](@ref), [`struct`](@ref), [`mutable struct`](@ref), [`begin`](@ref), [`let`](@ref), [`for`](@ref) usw.

`end` kann auch beim Indizieren verwendet werden, um den letzten Index einer Sammlung oder den letzten Index einer Dimension eines Arrays darzustellen.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64, 2}:
 1  2
 3  4

julia> A[end, :]
2-element Array{Int64, 1}:
 3
 4
```
