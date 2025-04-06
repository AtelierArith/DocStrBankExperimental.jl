```
Meta.show_sexpr([io::IO,], ex)
```

Zeigt den Ausdruck `ex` als lisp-artigen S-Ausdruck an.

# Beispiele

```jldoctest
julia> Meta.show_sexpr(:(f(x, g(y,z))))
(:call, :f, :x, (:call, :g, :y, :z))
```
