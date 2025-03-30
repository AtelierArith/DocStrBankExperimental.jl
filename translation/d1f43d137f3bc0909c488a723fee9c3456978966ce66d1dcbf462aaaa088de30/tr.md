```
Meta.show_sexpr([io::IO,], ex)
```

Gösterim ifadesi `ex`'i lisp tarzı S-ifadesi olarak gösterir.

# Örnekler

```jldoctest
julia> Meta.show_sexpr(:(f(x, g(y,z))))
(:call, :f, :x, (:call, :g, :y, :z))
```
