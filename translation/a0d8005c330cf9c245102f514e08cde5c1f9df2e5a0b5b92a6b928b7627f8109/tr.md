```
<:(T1, T2)
```

Alt türü operatörü: `T1` türündeki tüm değerlerin `T2` türünde de olduğu durumunda `true` döner.

# Örnekler

```jldoctest
julia> Float64 <: AbstractFloat
true

julia> Vector{Int} <: AbstractArray
true

julia> Matrix{Float64} <: Matrix{AbstractFloat}
false
```
