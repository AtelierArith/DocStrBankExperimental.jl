```
randn!([rng=default_rng()], A::AbstractArray) -> A
```

Llena el arreglo `A` con números aleatorios distribuidos normalmente (media 0, desviación estándar 1). También consulta la función [`rand`](@ref).

# Ejemplos

```jldoctest
julia> randn!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 -0.6457306721039767
 -1.4632513788889214
 -1.6236037455860806
 -0.21766510678354617
  0.4922456865251828
```
