```
real(T::Type)
```

Gibt den Typ zurück, der den Realteil eines Wertes des Typs `T` darstellt. z.B.: für `T == Complex{R}` gibt `R` zurück. Entspricht `typeof(real(zero(T)))`.

# Beispiele

```jldoctest
julia> real(Complex{Int})
Int64

julia> real(Float64)
Float64
```
