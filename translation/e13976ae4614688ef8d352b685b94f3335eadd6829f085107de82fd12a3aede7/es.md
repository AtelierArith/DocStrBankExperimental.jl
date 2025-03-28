```
oneunit(x::T)
oneunit(T::Type)
```

Devuelve `T(one(x))`, donde `T` es el tipo del argumento o (si se pasa un tipo) el argumento. Esto difiere de [`one`](@ref) para cantidades con dimensiones: `one` es adimensional (una identidad multiplicativa) mientras que `oneunit` es dimensional (del mismo tipo que `x`, o del tipo `T`).

# Ejemplos

```jldoctest
julia> oneunit(3.7)
1.0

julia> import Dates; oneunit(Dates.Day)
1 día
```
