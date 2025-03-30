```
nerede
```

`where` anahtar kelimesi, bazı değişkenlerin tüm değerleri üzerinde diğer türlerin yinelemeli birleşimi olarak düşünülebilecek bir [`UnionAll`](@ref) türü oluşturur. Örneğin, `Vector{T} where T<:Real`, eleman türü bir tür `Real` sayısı olan tüm [`Vector`](@ref)ları içerir.

Değişken bağı, atlanırsa varsayılan olarak [`Any`](@ref) olarak ayarlanır:

```julia
Vector{T} where T    # `where T<:Any` için kısadır
```

Değişkenler ayrıca alt sınırları da olabilir:

```julia
Vector{T} where T>:Int
Vector{T} where Int<:T<:Real
```

Ayrıca, iç içe `where` ifadeleri için de kısa bir sözdizimi vardır. Örneğin, bu:

```julia
Pair{T, S} where S<:Array{T} where T<:Number
```

şu şekilde kısaltılabilir:

```julia
Pair{T, S} where {T<:Number, S<:Array{T}}
```

Bu form genellikle yöntem imzalarında bulunur.

Bu formda, değişkenler en dıştaki ilk sırada listelenir. Bu, bir türün `T{p1, p2, ...}` sözdizimi kullanılarak parametre değerlerine "uygulanırken" değişkenlerin yer değiştirme sırasıyla eşleşir.
