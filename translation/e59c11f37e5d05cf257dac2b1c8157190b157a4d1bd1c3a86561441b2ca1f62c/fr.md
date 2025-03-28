```
@show exs...
```

Affiche une ou plusieurs expressions, ainsi que leurs résultats, sur `stdout`, et renvoie le dernier résultat.

Voir aussi : [`show`](@ref), [`@info`](@ref man-logging), [`println`](@ref).

# Exemples

```jldoctest
julia> x = @show 1+2
1 + 2 = 3
3

julia> @show x^2 x/2;
x ^ 2 = 9
x / 2 = 1.5
```
