```
real(T::Type)
```

Bir `T` türündeki bir değerin reel kısmını temsil eden türü döndürür. Örneğin: `T == Complex{R}` için `R` döner. `typeof(real(zero(T)))` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> real(Complex{Int})
Int64

julia> real(Float64)
Float64
```
