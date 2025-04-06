```
cat(A...; dims)
```

Girdi dizilerini `dims`'de belirtilen boyutlar boyunca birleştirir.

Bir `d` boyutunda `dims` içinde, çıktı dizisinin boyutu `sum(size(a,d) for a in A)`'dir. Diğer boyutlar boyunca, tüm girdi dizilerinin aynı boyutta olması gerekir; bu da o boyutlar boyunca çıktı dizisinin boyutunu belirler.

Eğer `dims` tek bir sayı ise, farklı diziler o boyut boyunca sıkı bir şekilde paketlenir. Eğer `dims` birden fazla boyut içeren bir iterable ise, bu boyutlar boyunca pozisyonlar her girdi dizisi için aynı anda artırılır ve diğer yerler sıfır ile doldurulur. Bu, `cat(matrices...; dims=(1,2))` şeklinde blok-diagonal matrisler oluşturmayı sağlar ve bunların daha yüksek boyutlu analoglarını da.

Özel durum `dims=1` [`vcat`](@ref) ve `dims=2` [`hcat`](@ref) olarak tanımlanır. Ayrıca [`hvcat`](@ref), [`hvncat`](@ref), [`stack`](@ref), [`repeat`](@ref) ile de bakılabilir.

Anahtar kelime ayrıca `Val(dims)`'i de kabul eder.

!!! compat "Julia 1.8"
    Birden fazla boyut için `dims = Val(::Tuple)` Julia 1.8'de eklendi.


# Örnekler

Farklı boyutlarda iki diziyi birleştirin:

```jldoctest
julia> a = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> b = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> cat(a, b; dims=1)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cat(a, b; dims=2)
1×6 Matrix{Int64}:
 1  2  3  4  5  6

julia> cat(a, b; dims=(1, 2))
2×6 Matrix{Int64}:
 1  2  3  0  0  0
 0  0  0  4  5  6
```

# Genişletilmiş Yardım

3D dizileri birleştirin:

```jldoctest
julia> a = ones(2, 2, 3);

julia> b = ones(2, 2, 4);

julia> c = cat(a, b; dims=3);

julia> size(c) == (2, 2, 7)
true
```

Farklı boyutlardaki dizileri birleştirin:

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # hcat ile aynı
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0
```

Bir blok diagonal matris oluşturun:

```
julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # blok-diagonal
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1
```

```
julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```

!!! note
    `cat` iki dizeyi birleştirmez, `*` kullanmak isteyebilirsiniz.


```jldoctest
julia> a = "aaa";

julia> b = "bbb";

julia> cat(a, b; dims=1)
2-element Vector{String}:
 "aaa"
 "bbb"

julia> cat(a, b; dims=2)
1×2 Matrix{String}:
 "aaa"  "bbb"

julia> a * b
"aaabbb"
```
