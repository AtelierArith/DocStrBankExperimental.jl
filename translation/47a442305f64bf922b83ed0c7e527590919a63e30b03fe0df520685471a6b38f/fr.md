```
fin
```

`fin` marque la conclusion d'un bloc d'expressions, par exemple [`module`](@ref), [`struct`](@ref), [`mutable struct`](@ref), [`begin`](@ref), [`let`](@ref), [`for`](@ref) etc.

`fin` peut également être utilisé lors de l'indexation pour représenter le dernier index d'une collection ou le dernier index d'une dimension d'un tableau.

# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64, 2}:
 1  2
 3  4

julia> A[fin, :]
2-element Array{Int64, 1}:
 3
 4
```
