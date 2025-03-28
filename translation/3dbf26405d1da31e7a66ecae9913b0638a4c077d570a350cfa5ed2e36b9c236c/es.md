```
Base.summarysize(obj; exclude=Union{...}, chargeall=Union{...}) -> Int
```

Calcula la cantidad de memoria, en bytes, utilizada por todos los objetos únicos accesibles desde el argumento.

# Argumentos Clave

  * `exclude`: especifica los tipos de objetos a excluir de la travesía.
  * `chargeall`: especifica los tipos de objetos a los que siempre se les cobrará el tamaño de todos sus campos, incluso si esos campos normalmente serían excluidos.

Véase también [`sizeof`](@ref).

# Ejemplos

```jldoctest
julia> Base.summarysize(1.0)
8

julia> Base.summarysize(Ref(rand(100)))
848

julia> sizeof(Ref(rand(100)))
8
```
