```
get!(f::Union{Function, Type}, collection, key)
```

Retourne la valeur stockée pour la clé donnée, ou si aucune correspondance pour la clé n'est présente, stocke `key => f()`, et retourne `f()`.

Ceci est destiné à être appelé en utilisant la syntaxe de bloc `do`.

# Exemples

```jldoctest
julia> squares = Dict{Int, Int}();

julia> function get_square!(d, i)
           get!(d, i) do
               i^2
           end
       end
get_square! (generic function with 1 method)

julia> get_square!(squares, 2)
4

julia> squares
Dict{Int64, Int64} with 1 entry:
  2 => 4
```
