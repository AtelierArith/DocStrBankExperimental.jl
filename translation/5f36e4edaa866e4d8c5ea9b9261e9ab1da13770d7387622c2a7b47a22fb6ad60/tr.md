```
nfields(x) -> Int
```

Verilen nesnedeki alan sayısını alır.

# Örnekler

```jldoctest
julia> a = 1//2;

julia> nfields(a)
2

julia> b = 1
1

julia> nfields(b)
0

julia> ex = ErrorException("Kötü bir şey yaptım");

julia> nfields(ex)
1
```

Bu örneklerde, `a` bir [`Rational`](@ref) olup iki alana sahiptir. `b` bir `Int` olup hiç alanı olmayan bir ilkel bit türüdür. `ex` bir [`ErrorException`](@ref) olup bir alana sahiptir.
