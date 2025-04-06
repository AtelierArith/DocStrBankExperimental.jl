```
@inbounds(blk)
```

Dizi sınır kontrolünü ifadeler içinde ortadan kaldırır.

Aşağıdaki örnekte, dizi `A`'nın `i` elemanına referans verirken aralık kontrolü atlanır ve bu da performansı artırır.

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

!!! uyarı     `@inbounds` kullanmak, sınır dışı indeksler için yanlış sonuçlar/çökmeler/bozulmalar döndürebilir. Kullanıcı, bunu manuel olarak kontrol etmekten sorumludur. `@inbounds` yalnızca, yerel olarak mevcut bilgilerden tüm erişimlerin sınır içinde olduğundan emin olunduğunda kullanılmalıdır. Özellikle, yukarıdaki gibi bir işlevde `eachindex(A)` yerine `1:length(A)` kullanmak *güvenli bir şekilde sınır içinde* değildir çünkü `A`'nın ilk indeksi, `AbstractArray`'ı alt tür olarak tanımlayan tüm kullanıcı tanımlı türler için `1` olmayabilir.
