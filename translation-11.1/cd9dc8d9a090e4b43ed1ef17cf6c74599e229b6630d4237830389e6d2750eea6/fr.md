```
floatmin(T = Float64)
```

Renvoie le plus petit nombre normal positif représentable par le type à virgule flottante `T`.

# Exemples

```jldoctest
julia> floatmin(Float16)
Float16(6.104e-5)

julia> floatmin(Float32)
1.1754944f-38

julia> floatmin()
2.2250738585072014e-308
```
