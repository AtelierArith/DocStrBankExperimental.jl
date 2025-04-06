```
fullname(m::Module)
```

Holen Sie sich den vollqualifizierten Namen eines Moduls als Tupel von Symbolen. Zum Beispiel,

# Beispiele

```jldoctest
julia> fullname(Base.Iterators)
(:Base, :Iterators)

julia> fullname(Main)
(:Main,)
```
