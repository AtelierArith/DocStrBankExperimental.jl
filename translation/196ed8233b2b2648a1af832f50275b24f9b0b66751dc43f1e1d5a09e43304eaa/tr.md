```
typejoin(T, S, ...)
```

`T` ve `S` türlerinin en yakın ortak atasını döndürür, yani her ikisinin de miras aldığı en dar türü. Ek varargs üzerinde yinelemeler yapar.

# Örnekler

```jldoctest
julia> typejoin(Int, Float64)
Real

julia> typejoin(Int, Float64, ComplexF32)
Number
```
