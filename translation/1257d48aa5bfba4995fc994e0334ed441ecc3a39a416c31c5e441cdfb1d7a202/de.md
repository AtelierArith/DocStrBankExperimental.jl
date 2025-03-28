```
unique!(f, A::AbstractVector)
```

Wählt einen Wert aus `A` für jeden einzigartigen Wert, der durch `f` erzeugt wird, angewendet auf die Elemente von `A`, und gibt dann das modifizierte A zurück.

!!! compat "Julia 1.1"
    Diese Methode ist seit Julia 1.1 verfügbar.


# Beispiele

```jldoctest
julia> unique!(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4

julia> unique!(n -> n%3, [5, 1, 8, 9, 3, 4, 10, 7, 2, 6])
3-element Vector{Int64}:
 5
 1
 9

julia> unique!(iseven, [2, 3, 5, 7, 9])
2-element Vector{Int64}:
 2
 3
```
