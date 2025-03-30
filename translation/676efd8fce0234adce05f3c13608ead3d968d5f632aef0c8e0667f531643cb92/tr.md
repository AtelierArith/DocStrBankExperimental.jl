```
stack(iter; [dims])
```

Eşit boyutlara sahip bir dizi (veya diğer yineleyici nesneler) koleksiyonunu, bir veya daha fazla yeni boyut boyunca düzenleyerek daha büyük bir dizi haline getirir.

Varsayılan olarak, elemanların eksenleri önce yerleştirilir, bu da `size(result) = (size(first(iter))..., size(iter)...)` sonucunu verir. Bu, [`Iterators.flatten`](@ref)`(iter)` ile aynı eleman sırasına sahiptir.

`dims::Integer` anahtar kelimesi ile, `iter`'in `i`'nci elemanı, `result`'ın dilimlerini [`selectdim`](@ref)`(result, dims, i)` haline getirir, böylece `size(result, dims) == length(iter)` olur. Bu durumda `stack`, aynı `dims` ile [`eachslice`](@ref)` işleminin tersini gerçekleştirir.

Çeşitli [`cat`](@ref) fonksiyonları da dizileri birleştirir. Ancak, bunlar dizilerin mevcut (belki de önemsiz) boyutlarını uzatır, yeni boyutlar boyunca dizileri yerleştirmek yerine. Ayrıca, dizileri ayrı argümanlar olarak kabul ederler, tek bir koleksiyon yerine.

!!! compat "Julia 1.9"
    Bu fonksiyon en az Julia 1.9 gerektirir.


# Örnekler

```jldoctest
julia> vecs = (1:2, [30, 40], Float32[500, 600]);

julia> mat = stack(vecs)
2×3 Matrix{Float32}:
 1.0  30.0  500.0
 2.0  40.0  600.0

julia> mat == hcat(vecs...) == reduce(hcat, collect(vecs))
true

julia> vec(mat) == vcat(vecs...) == reduce(vcat, collect(vecs))
true

julia> stack(zip(1:4, 10:99))  # her türlü yineleyici kabul eder
2×4 Matrix{Int64}:
  1   2   3   4
 10  11  12  13

julia> vec(ans) == collect(Iterators.flatten(zip(1:4, 10:99)))
true

julia> stack(vecs; dims=1)  # herhangi bir cat fonksiyonunun aksine, vecs[1]'in 1. ekseni sonucun 2. eksenidir
3×2 Matrix{Float32}:
   1.0    2.0
  30.0   40.0
 500.0  600.0

julia> x = rand(3,4);

julia> x == stack(eachcol(x)) == stack(eachrow(x), dims=1)  # eachslice'in tersidir
true
```

Daha yüksek boyutlu örnekler:

```jldoctest
julia> A = rand(5, 7, 11);

julia> E = eachslice(A, dims=2);  # matrislerin bir vektörü

julia> (element = size(first(E)), container = size(E))
(element = (5, 11), container = (7,))

julia> stack(E) |> size
(5, 11, 7)

julia> stack(E) == stack(E; dims=3) == cat(E...; dims=3)
true

julia> A == stack(E; dims=2)
true

julia> M = (fill(10i+j, 2, 3) for i in 1:5, j in 1:7);

julia> (element = size(first(M)), container = size(M))
(element = (2, 3), container = (5, 7))

julia> stack(M) |> size  # tüm boyutları korur
(2, 3, 5, 7)

julia> stack(M; dims=1) |> size  # vec(container) boyutları boyunca
(35, 2, 3)

julia> hvcat(5, M...) |> size  # hvcat matrisleri yan yana koyar
(14, 15)
```
