```
Meta.show_sexpr([io::IO,], ex)
```

Afficher l'expression `ex` sous forme d'une S-expression de style lisp.

# Exemples

```jldoctest
julia> Meta.show_sexpr(:(f(x, g(y,z))))
(:call, :f, :x, (:call, :g, :y, :z))
```
