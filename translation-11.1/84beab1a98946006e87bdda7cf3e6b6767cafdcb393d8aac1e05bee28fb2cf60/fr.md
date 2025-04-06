```
local
```

`local` introduit une nouvelle variable locale. Voir la [section du manuel sur la portée des variables](@ref scope-of-variables) pour plus d'informations.

# Exemples

```jldoctest
julia> function foo(n)
           x = 0
           for i = 1:n
               local x # introduire un x local à la boucle
               x = i
           end
           x
       end
foo (generic function with 1 method)

julia> foo(10)
0
```
