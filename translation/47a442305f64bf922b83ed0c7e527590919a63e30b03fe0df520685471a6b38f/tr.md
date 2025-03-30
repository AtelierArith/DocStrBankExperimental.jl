```
end
```

`end`, bir ifade bloğunun sonunu işaret eder; örneğin [`module`](@ref), [`struct`](@ref), [`mutable struct`](@ref), [`begin`](@ref), [`let`](@ref), [`for`](@ref) vb.

`end`, ayrıca bir koleksiyonun son indeksini veya bir dizinin son indeksini temsil etmek için indeksleme sırasında da kullanılabilir.

# Örnekler

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
