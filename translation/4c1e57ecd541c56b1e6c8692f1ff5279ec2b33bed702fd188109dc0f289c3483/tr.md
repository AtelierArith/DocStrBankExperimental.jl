```
cumsum(A; dims::Integer)
```

Boyut `dims` boyunca kümülatif toplam. Önceden tahsis edilmiş bir çıktı dizisi kullanmak için [`cumsum!`](@ref) ile birlikte performans ve çıktının hassasiyetini kontrol etmek için de kullanılabilir (örneğin, taşmayı önlemek için).

# Örnekler

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! not
    Dönüş dizisinin `eltype`'i, sistem kelime boyutundan daha küçük işaretli tam sayılar için `Int` ve sistem kelime boyutundan daha küçük işaretsiz tam sayılar için `UInt`'dir. Küçük işaretli veya işaretsiz tam sayıların `eltype`'ini korumak için `accumulate(+, A)` kullanılmalıdır.

    ```jldoctest
    julia> cumsum(Int8[100, 28])
    2-element Vector{Int64}:
     100
     128

    julia> accumulate(+,Int8[100, 28])
    2-element Vector{Int8}:
      100
     -128
    ```

    İlk durumda, tam sayılar sistem kelime boyutuna genişletilir ve bu nedenle sonuç `Int64[100, 128]` olur. İkinci durumda, böyle bir genişletme gerçekleşmez ve tam sayı taşması `Int8[100, -128]` sonucunu verir.

