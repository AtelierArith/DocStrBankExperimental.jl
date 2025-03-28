```
signbit(x)
```

Gibt `true` zurück, wenn der Wert des Vorzeichens von `x` negativ ist, andernfalls `false`.

Siehe auch [`sign`](@ref) und [`copysign`](@ref).

# Beispiele

```jldoctest
julia> signbit(-4)
true

julia> signbit(5)
false

julia> signbit(5.5)
false

julia> signbit(-4.1)
true
```
