```
Meta.show_sexpr([io::IO,], ex)
```

Muestra la expresión `ex` como una S-expresión al estilo lisp.

# Ejemplos

```jldoctest
julia> Meta.show_sexpr(:(f(x, g(y,z))))
(:call, :f, :x, (:call, :g, :y, :z))
```
