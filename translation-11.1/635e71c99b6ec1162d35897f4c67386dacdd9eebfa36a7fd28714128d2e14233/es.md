```
fullname(m::Module)
```

Obtiene el nombre completamente calificado de un módulo como una tupla de símbolos. Por ejemplo,

# Ejemplos

```jldoctest
julia> fullname(Base.Iterators)
(:Base, :Iterators)

julia> fullname(Main)
(:Main,)
```
