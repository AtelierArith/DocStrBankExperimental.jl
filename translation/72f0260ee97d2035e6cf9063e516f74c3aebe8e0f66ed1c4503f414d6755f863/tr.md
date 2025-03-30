```
vcat(A...)
```

Dizileri veya sayıları dikey olarak birleştirir. [`cat`](@ref)`(A...; dims=1)` ile eşdeğerdir ve `[a; b; c]` sözdizimine eşdeğerdir.

Büyük bir dizi dizisini birleştirmek için, `reduce(vcat, A)` `A isa AbstractVector{<:AbstractVecOrMat}` olduğunda verimli bir yöntem çağırır, çiftler halinde çalışmak yerine.

Ayrıca [`hcat`](@ref), [`Iterators.flatten`](@ref), [`stack`](@ref) ile de ilgili.

# Örnekler

```jldoctest
julia> v = vcat([1,2], [3,4])
4-element Vector{Int64}:
 1
 2
 3
 4

julia> v == vcat(1, 2, [3,4])  # sayıları kabul eder
true

julia> v == [1; 2; [3,4]]  # aynı işlemi yapmak için sözdizimi
true

julia> summary(ComplexF64[1; 2; [3,4]])  # eleman türünü sağlamak için sözdizimi
"4-element Vector{ComplexF64}"

julia> vcat(range(1, 2, length=3))  # tembel aralıkları toplar
3-element Vector{Float64}:
 1.0
 1.5
 2.0

julia> two = ([10, 20, 30]', Float64[4 5 6; 7 8 9])  # satır vektörü ve bir matris
([10 20 30], [4.0 5.0 6.0; 7.0 8.0 9.0])

julia> vcat(two...)
3×3 Matrix{Float64}:
 10.0  20.0  30.0
  4.0   5.0   6.0
  7.0   8.0   9.0

julia> vs = [[1, 2], [3, 4], [5, 6]];

julia> reduce(vcat, vs)  # vcat(vs...)' den daha verimli
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> ans == collect(Iterators.flatten(vs))
true
```
