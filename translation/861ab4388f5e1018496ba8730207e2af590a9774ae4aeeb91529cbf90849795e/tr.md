```
permutedims(A::AbstractArray, perm)
permutedims(A::AbstractMatrix)
```

Dizinin boyutlarını (ekseni) `A` dizisinde permütasyon yapın. `perm`, `ndims(A)` tamsayılarından oluşan bir demet veya vektördür ve permütasyonu belirtir.

Eğer `A` 2 boyutlu bir dizi ([`AbstractMatrix`](@ref)) ise, `perm` varsayılan olarak `(2,1)` değerini alır ve `A`'nın iki eksenini (matrisin satır ve sütunlarını) değiştirir. Bu, [`transpose`](@ref) ile farklıdır çünkü işlem özyinelemeli değildir; bu, özellikle özyinelemeli `transpose` hataya neden olacağı için sayısal olmayan değerler içeren diziler ve/veya lineer operatörleri temsil etmeyen 2 boyutlu diziler için özellikle yararlıdır.

1 boyutlu diziler için [`permutedims(v::AbstractVector)`](@ref) bakın; bu, 1 satırlık bir “matris” döndürür.

Ayrıca [`permutedims!`](@ref), [`PermutedDimsArray`](@ref), [`transpose`](@ref), [`invperm`](@ref) ile ilgili daha fazla bilgiye bakın.

# Örnekler

## 2 boyutlu diziler:

`transpose`'dan farklı olarak, `permutedims`, 2 boyutlu dizilerin satır ve sütunlarını, örneğin dizeler gibi, rastgele sayısal olmayan elemanlarla değiştirmek için kullanılabilir:

```jldoctest
julia> A = ["a" "b" "c"
            "d" "e" "f"]
2×3 Matrix{String}:
 "a"  "b"  "c"
 "d"  "e"  "f"

julia> permutedims(A)
3×2 Matrix{String}:
 "a"  "d"
 "b"  "e"
 "c"  "f"
```

Ve `permutedims`, elemanları kendileri sayısal matrisler olan matrisler için `transpose`'dan farklı sonuçlar üretir:

```jldoctest; setup = :(using LinearAlgebra)
julia> a = [1 2; 3 4];

julia> b = [5 6; 7 8];

julia> c = [9 10; 11 12];

julia> d = [13 14; 15 16];

julia> X = [[a] [b]; [c] [d]]
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]     [5 6; 7 8]
 [9 10; 11 12]  [13 14; 15 16]

julia> permutedims(X)
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [9 10; 11 12]
 [5 6; 7 8]  [13 14; 15 16]

julia> transpose(X)
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [9 11; 10 12]
 [5 7; 6 8]  [13 15; 14 16]
```

## Çok boyutlu diziler

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # son boyutu ilk sıraya koy

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # ters permütasyon
true
```

`B = permutedims(A, perm)` için her bir boyut `i`'de, `A`'nın karşılık gelen boyutu `perm[i]` olacaktır. Bu, `size(B, i) == size(A, perm[i])` eşitliğinin geçerli olduğu anlamına gelir.

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
