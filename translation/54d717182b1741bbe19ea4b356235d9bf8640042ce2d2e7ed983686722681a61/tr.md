```
hcat(A...)
```

Dizileri veya sayıları yatay olarak birleştirir. [`cat`](@ref)`(A...; dims=2)` ile eşdeğerdir ve `[a b c]` veya `[a;; b;; c]` sözdizimine eşdeğerdir.

Büyük bir dizi vektörü için, `reduce(hcat, A)` `A isa AbstractVector{<:AbstractVecOrMat}` olduğunda verimli bir yöntemi çağırır. Vektörler için bu ayrıca [`stack`](@ref)`(A)` olarak da yazılabilir.

Ayrıca [`vcat`](@ref), [`hvcat`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> hcat([1,2], [3,4], [5,6])
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> hcat(1, 2, [30 40], [5, 6, 7]')  # sayıları kabul eder
1×7 Matrix{Int64}:
 1  2  30  40  5  6  7

julia> ans == [1 2 [30 40] [5, 6, 7]']  # aynı işlemi yapmak için sözdizimi
true

julia> Float32[1 2 [30 40] [5, 6, 7]']  # eltipi sağlamak için sözdizimi
1×7 Matrix{Float32}:
 1.0  2.0  30.0  40.0  5.0  6.0  7.0

julia> ms = [zeros(2,2), [1 2; 3 4], [50 60; 70 80]];

julia> reduce(hcat, ms)  # hcat(ms...)'ten daha verimli
2×6 Matrix{Float64}:
 0.0  0.0  1.0  2.0  50.0  60.0
 0.0  0.0  3.0  4.0  70.0  80.0

julia> stack(ms) |> summary  # matris vektörü üzerinde anlaşmazlık
"2×2×3 Array{Float64, 3}"

julia> hcat(Int[], Int[], Int[])  # boyutu (0,) olan boş vektörler
0×3 Matrix{Int64}

julia> hcat([1.1, 9.9], Matrix(undef, 2, 0))  # boş 2×0 Matris ile hcat
2×1 Matrix{Any}:
 1.1
 9.9
```
