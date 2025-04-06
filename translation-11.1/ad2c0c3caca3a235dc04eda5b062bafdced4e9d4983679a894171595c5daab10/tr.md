```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

Yerinde versiyonu [`shuffle`](@ref): `v`'yi yerinde rastgele permüte eder, isteğe bağlı olarak rastgele sayı üreteci `rng` sağlanabilir.

# Örnekler

```jldoctest
julia> shuffle!(Xoshiro(123), Vector(1:10))
10-element Vector{Int64}:
  5
  4
  2
  3
  6
 10
  8
  1
  9
  7
```
