```
begin
```

`begin...end` désigne un bloc de code.

```julia
begin
    println("Hello, ")
    println("World!")
end
```

En général, `begin` ne sera pas nécessaire, car des mots-clés tels que [`function`](@ref) et [`let`](@ref) commencent implicitement des blocs de code. Voir aussi [`;`](@ref).

`begin` peut également être utilisé lors de l'indexation pour représenter le premier index d'une collection ou le premier index d'une dimension d'un tableau. Par exemple, `a[begin]` est le premier élément d'un tableau `a`.

!!! compat "Julia 1.4"
    L'utilisation de `begin` comme index nécessite Julia 1.4 ou une version ultérieure.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64,2}:
 1  2
 3  4

julia> A[begin, :]
2-element Array{Int64,1}:
 1
 2
```
