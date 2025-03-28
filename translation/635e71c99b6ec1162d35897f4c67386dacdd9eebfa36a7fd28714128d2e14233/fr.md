```
fullname(m::Module)
```

Obtenez le nom entièrement qualifié d'un module sous forme de tuple de symboles. Par exemple,

# Exemples

```jldoctest
julia> fullname(Base.Iterators)
(:Base, :Iterators)

julia> fullname(Main)
(:Main,)
```
