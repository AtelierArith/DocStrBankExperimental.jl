```
Expr(head::Symbol, args...)
```

Un type représentant des expressions composées dans le code julia analysé (ASTs). Chaque expression se compose d'un `head` `Symbol` identifiant quel type d'expression il s'agit (par exemple, un appel, une boucle for, une instruction conditionnelle, etc.), et de sous-expressions (par exemple, les arguments d'un appel). Les sous-expressions sont stockées dans un champ `Vector{Any}` appelé `args`.

Voir le chapitre du manuel sur [Metaprogramming](@ref) et la documentation des développeurs [Julia ASTs](@ref).

# Exemples

```jldoctest
julia> Expr(:call, :+, 1, 2)
:(1 + 2)

julia> dump(:(a ? b : c))
Expr
  head: Symbol if
  args: Array{Any}((3,))
    1: Symbol a
    2: Symbol b
    3: Symbol c
```
