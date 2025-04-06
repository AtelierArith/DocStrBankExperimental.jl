```
in!(x, s::AbstractSet) -> Bool
```

Wenn `x` in `s` ist, gibt `true` zurück. Andernfalls wird `x` in `s` eingefügt und `false` zurückgegeben. Dies ist äquivalent zu `in(x, s) ? true : (push!(s, x); false)`, könnte jedoch eine effizientere Implementierung haben.

Siehe auch: [`in`](@ref), [`push!`](@ref), [`Set`](@ref)

!!! compat "Julia 1.11"
    Diese Funktion erfordert mindestens 1.11.


# Beispiele

```jldoctest; filter = r"^  [1234]$"
julia> s = Set{Any}([1, 2, 3]); in!(4, s)
false

julia> length(s)
4

julia> in!(0x04, s)
true

julia> s
Set{Any} mit 4 Elementen:
  4
  2
  3
  1
```
