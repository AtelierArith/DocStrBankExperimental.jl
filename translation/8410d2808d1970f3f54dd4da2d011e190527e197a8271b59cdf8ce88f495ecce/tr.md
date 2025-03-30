```
reduce(f, A::AbstractArray; dims=:, [init])
```

`A`'n boyutları boyunca `f` 2-argümanlı fonksiyonunu azalt. `dims`, azaltılacak boyutları belirten bir vektördür ve `init` anahtar kelime argümanı, azaltmalarda kullanılacak başlangıç değeridir. `+`, `*`, `max` ve `min` için `init` argümanı isteğe bağlıdır.

Azaltmanın birleşim özelliği uygulamaya bağlıdır; belirli bir birleşim özelliğine ihtiyacınız varsa, örneğin soldan sağa, kendi döngünüzü yazmalısınız veya [`foldl`](@ref) veya [`foldr`](@ref) kullanmayı düşünmelisiniz. [`reduce`](@ref) için belgeleri inceleyin.

# Örnekler

```jldoctest
julia> a = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reduce(max, a, dims=2)
4×1 Matrix{Int64}:
 13
 14
 15
 16

julia> reduce(max, a, dims=1)
1×4 Matrix{Int64}:
 4  8  12  16
```
