```
x || y
```

Kısa devre boolean VEYA.

Ayrıca bakınız: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Örnekler

```jldoctest
julia> pi < 3 || ℯ < 3
true

julia> false || true || println("hiçbiri doğru değil!")
true
```
