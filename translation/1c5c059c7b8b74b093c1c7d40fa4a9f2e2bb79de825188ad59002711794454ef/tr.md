```
IndexCartesian()
```

[`IndexStyle`](@ref) alt türü, Cartesian indeksi ile optimal olarak indekslenen dizileri tanımlamak için kullanılır. Bu, yeni özel [`AbstractArray`](@ref) alt türleri için varsayılandır.

Bir Cartesian indeksleme stili, çok boyutlu bir dizideki konumu tanımlamak için birden fazla tam sayı indeksi kullanır ve her boyut için tam olarak bir indeks bulunur. Bu, `IndexCartesian` olan bir diziden [`eachindex`](@ref) talep edildiğinde, bir dizi [`CartesianIndices`](@ref) döneceği anlamına gelir.

`IndexCartesian` olarak `IndexStyle`'ını bildiren `N` boyutlu özel bir dizinin, tam olarak `N` `Int` indeksi ile indeksleme (ve indeksli atama) uygulaması gerekir; diğer tüm indeksleme ifadeleri — lineer indeksleme dahil — eşdeğer Cartesian konumuna yeniden hesaplanacaktır. Örneğin, `A` bir Cartesian indeksleme ile `2×3` özel bir matris olsaydı ve `A[5]` referans verilseydi, bu eşdeğer Cartesian indeksi olarak yeniden hesaplanacak ve `A[1, 3]` çağrılacaktır çünkü `5 = 1 + 2*(3 - 1)`.

Lineer bir indeksten Cartesian indeksleri hesaplamak, tersine gitmekten çok daha pahalıdır. İlk işlem bölme gerektirir — çok maliyetli bir işlem — oysa ikincisi yalnızca çarpma ve toplama kullanır ve esasen ücretsizdir. Bu asimetri, `IndexCartesian` dizisi ile lineer indeksleme kullanmanın, `IndexLinear` dizisi ile Cartesian indeksleme kullanmaktan çok daha maliyetli olduğu anlamına gelir.

Ayrıca bkz. [`IndexLinear`](@ref).
