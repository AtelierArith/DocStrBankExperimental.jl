```
repeat(A::AbstractArray, counts::Integer...)
```

Diziyi `A`'yı her boyutta belirtilen `counts` sayısı kadar tekrar ederek bir dizi oluşturur.

Ayrıca bakınız: [`fill`](@ref), [`Iterators.repeated`](@ref), [`Iterators.cycle`](@ref).

# Örnekler

```jldoctest
julia> repeat([1, 2, 3], 2)
6-element Vector{Int64}:
 1
 2
 3
 1
 2
 3

julia> repeat([1, 2, 3], 2, 3)
6×3 Matrix{Int64}:
 1  1  1
 2  2  2
 3  3  3
 1  1  1
 2  2  2
 3  3  3
```
