```
begin
```

`begin...end` bezeichnet einen Codeblock.

```julia
begin
    println("Hallo, ")
    println("Welt!")
end
```

Normalerweise ist `begin` nicht notwendig, da Schlüsselwörter wie [`function`](@ref) und [`let`](@ref) implizit Codeblöcke beginnen. Siehe auch [`;`](@ref).

`begin` kann auch beim Indizieren verwendet werden, um den ersten Index einer Sammlung oder den ersten Index einer Dimension eines Arrays darzustellen. Zum Beispiel ist `a[begin]` das erste Element eines Arrays `a`.

!!! compat "Julia 1.4"
    Die Verwendung von `begin` als Index erfordert Julia 1.4 oder später.


# Beispiele

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
