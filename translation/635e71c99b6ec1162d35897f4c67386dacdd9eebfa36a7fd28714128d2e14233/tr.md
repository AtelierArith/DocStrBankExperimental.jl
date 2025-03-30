```
fullname(m::Module)
```

Bir modülün tam nitelikli adını semboller tuple'ı olarak alır. Örneğin,

# Örnekler

```jldoctest
julia> fullname(Base.Iterators)
(:Base, :Iterators)

julia> fullname(Main)
(:Main,)
```
