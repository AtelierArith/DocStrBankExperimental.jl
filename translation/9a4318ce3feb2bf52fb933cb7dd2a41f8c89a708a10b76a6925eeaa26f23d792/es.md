```
real(T::Type)
```

Devuelve el tipo que representa la parte real de un valor del tipo `T`. por ejemplo: para `T == Complex{R}`, devuelve `R`. Equivalente a `typeof(real(zero(T)))`.

# Ejemplos

```jldoctest
julia> real(Complex{Int})
Int64

julia> real(Float64)
Float64
```
