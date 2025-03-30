```
permutedims(v::AbstractVector)
```

Vektörü `v` `1 × length(v)` satır matrisine yeniden şekillendirir. [`transpose`](@ref) ile farklıdır çünkü işlem özyinelemeli değildir; bu, özellikle özyinelemeli `transpose`'ın hata verebileceği sayısal olmayan değerlerin dizileri için özellikle yararlıdır.

# Örnekler

`transpose`'dan farklı olarak, `permutedims` rastgele sayısal olmayan öğelerin vektörlerinde, örneğin dizelerde kullanılabilir:

```jldoctest
julia> permutedims(["a", "b", "c"])
1×3 Matrix{String}:
 "a"  "b"  "c"
```

Sayılardan oluşan vektörler için, `permutedims(v)` `transpose(v)` ile çok benzer şekilde çalışır, tek fark dönüş türünün farklı olmasıdır (bir `LinearAlgebra.Transpose` görünümü yerine [`reshape`](@ref) kullanır, ancak her ikisi de orijinal dizi `v` ile belleği paylaşır):

```jldoctest; setup = :(using LinearAlgebra)
julia> v = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> p = permutedims(v)
1×4 Matrix{Int64}:
 1  2  3  4

julia> r = transpose(v)
1×4 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3  4

julia> p == r
true

julia> typeof(r)
Transpose{Int64, Vector{Int64}}

julia> p[1] = 5; r[2] = 6; # p veya r'yi değiştirmek v'yi de değiştirir

julia> v # hem p hem de r ile belleği paylaşır
4-element Vector{Int64}:
 5
 6
 3
 4
```

Ancak, `permutedims` sayısal matrislerden oluşan vektörler için `transpose`'dan farklı sonuçlar üretir:

```jldoctest; setup = :(using LinearAlgebra)
julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
