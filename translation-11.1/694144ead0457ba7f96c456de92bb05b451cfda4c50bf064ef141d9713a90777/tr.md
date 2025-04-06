```
pairs(IndexLinear(), A)
pairs(IndexCartesian(), A)
pairs(IndexStyle(A), A)
```

Dizi `A`'nın her bir elemanına erişen bir iteratör, `i => x` döndürür; burada `i` elemanın indeksi ve `x = A[i]`'dir. `pairs(A)` ile aynı, tek farkı indeks stilinin seçilebilmesidir. Ayrıca `enumerate(A)` ile de benzer, ancak `i` `A` için geçerli bir indeks olacaktır, oysa `enumerate` her zaman 1'den sayar, `A`'nın indekslerine bakılmaksızın.

[`IndexLinear()`](@ref) belirtmek, `i`'nin bir tam sayı olmasını garanti eder; [`IndexCartesian()`](@ref) belirtmek, `i`'nin bir [`Base.CartesianIndex`](@ref) olmasını garanti eder; `IndexStyle(A)` belirtmek, dizi `A` için tanımlanmış olan yerel indeksleme stilini seçer.

Temel dizinin sınırlarının değiştirilmesi bu iteratörü geçersiz kılacaktır.

# Örnekler

```jldoctest
julia> A = ["a" "d"; "b" "e"; "c" "f"];

julia> for (index, value) in pairs(IndexStyle(A), A)
           println("$index $value")
       end
1 a
2 b
3 c
4 d
5 e
6 f

julia> S = view(A, 1:2, :);

julia> for (index, value) in pairs(IndexStyle(S), S)
           println("$index $value")
       end
CartesianIndex(1, 1) a
CartesianIndex(2, 1) b
CartesianIndex(1, 2) d
CartesianIndex(2, 2) e
```

Ayrıca bkz. [`IndexStyle`](@ref), [`axes`](@ref).
