```
rem(x::Integer, T::Type{<:Integer}) -> T
mod(x::Integer, T::Type{<:Integer}) -> T
%(x::Integer, T::Type{<:Integer}) -> T
```

Encuentra `y::T` tal que `x` ≡ `y` (mod n), donde n es el número de enteros representables en `T`, y `y` es un entero en `[typemin(T),typemax(T)]`. Si `T` puede representar cualquier entero (por ejemplo, `T == BigInt`), entonces esta operación corresponde a una conversión a `T`.

# Ejemplos

```jldoctest
julia> x = 129 % Int8
-127

julia> typeof(x)
Int8

julia> x = 129 % BigInt
129

julia> typeof(x)
BigInt
```
