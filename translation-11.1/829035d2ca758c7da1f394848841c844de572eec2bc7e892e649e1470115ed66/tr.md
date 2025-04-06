```
IndexLinear()
```

Tekil bir indeksle tanımlanan dizileri tanımlamak için kullanılan [`IndexStyle`](@ref) alt türü.

Bir doğrusal indeksleme stili, dizideki konumu tanımlamak için bir tam sayı indeksi kullanır (çok boyutlu bir dizi olsa bile) ve elemanlara verimli bir şekilde erişmek için sütun-ana sıralama kullanılır. Bu, `IndexLinear` olan bir diziden [`eachindex`](@ref) istemenin, çok boyutlu olsa bile basit bir tek boyutlu aralık döndüreceği anlamına gelir.

`IndexStyle`'ını `IndexLinear` olarak bildiren özel bir dizi, yalnızca tek bir `Int` indeksi ile indeksleme (ve indeksli atama) uygulamak zorundadır; diğer tüm indeksleme ifadeleri — çok boyutlu erişimler de dahil — doğrusal indekse yeniden hesaplanacaktır. Örneğin, `A` doğrusal indeksleme ile `2×3` özel bir matris olsaydı ve `A[1, 3]` referansını alsaydık, bu, eşdeğer doğrusal indekse yeniden hesaplanacak ve `A[5]` çağrılacaktır çünkü `1 + 2*(3 - 1) = 5`.

Ayrıca bkz. [`IndexCartesian`](@ref).
