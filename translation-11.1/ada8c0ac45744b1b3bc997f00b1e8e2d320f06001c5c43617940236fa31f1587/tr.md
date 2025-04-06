```
@assert cond [metin]
```

`cond` `false` ise bir [`AssertionError`](@ref) fırlatır. Bu, kullanıcıların hata ayıklama yardımı olarak kontrol etmeyi tercih edebileceği, doğru olduğu varsayılan koşullar için yazılan assertions için tercih edilen sözdizimidir. İsteğe bağlı mesaj `metin`, assertion başarısız olduğunda görüntülenir.

!!! uyarı     Bir assert bazı optimizasyon seviyelerinde devre dışı bırakılabilir. Bu nedenle, assert yalnızca bir hata ayıklama aracı olarak kullanılmalı ve kimlik doğrulama doğrulaması (örneğin, şifreleri doğrulama veya dizi sınırlarını kontrol etme) için kullanılmamalıdır. Kod, bir fonksiyonun doğru davranışı için `cond`'un çalıştırılmasının yan etkilerine güvenmemelidir.

# Örnekler

```jldoctest
julia> @assert iseven(3) "3 bir tek sayıdır!"
HATA: AssertionError: 3 bir tek sayıdır!

julia> @assert isodd(3) "Sayılara ne kadar tek bile olsa?"
```
