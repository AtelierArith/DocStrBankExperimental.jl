```
rem(x::Integer, T::Type{<:Integer}) -> T
mod(x::Integer, T::Type{<:Integer}) -> T
%(x::Integer, T::Type{<:Integer}) -> T
```

Finde `y::T`, so dass `x` ≡ `y` (mod n), wobei n die Anzahl der in `T` darstellbaren Ganzzahlen ist und `y` eine Ganzzahl in `[typemin(T),typemax(T)]` ist. Wenn `T` jede Ganzzahl darstellen kann (z. B. `T == BigInt`), entspricht diese Operation einer Umwandlung in `T`.

# Beispiele

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
