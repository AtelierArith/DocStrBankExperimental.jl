```
nfields(x) -> Int
```

Obtiene el número de campos en el objeto dado.

# Ejemplos

```jldoctest
julia> a = 1//2;

julia> nfields(a)
2

julia> b = 1
1

julia> nfields(b)
0

julia> ex = ErrorException("He hecho algo malo");

julia> nfields(ex)
1
```

En estos ejemplos, `a` es un [`Rational`](@ref), que tiene dos campos. `b` es un `Int`, que es un tipo de bit primitivo sin campos en absoluto. `ex` es un [`ErrorException`](@ref), que tiene un campo.
