```
print_table([io::IO, ]register; digits::Int=5)
```

Print configuration-amplitude pairs of the `register`.

```jldoctest; setup=:(using Yao)
julia> reg = ghz_state(2);

julia> print_table(ghz_state(2))
00 ₍₂₎   0.70711 - 0.0im
01 ₍₂₎   0.0 + 0.0im
10 ₍₂₎   0.0 + 0.0im
11 ₍₂₎   0.70711 - 0.0im
```
