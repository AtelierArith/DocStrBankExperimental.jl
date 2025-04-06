```
serialize(stream::IO, value)
```

Bir akışa, [`deserialize`](@ref) ile geri okunabilecek opak bir formatta rastgele bir değer yazın. Geri okunan değer, mümkün olduğunca orijinaline benzer olacaktır, ancak `Ptr` değerlerinin tüm sıfır bit desenleri (`NULL`) olarak serileştirildiğini unutmayın.

Öncelikle akışa 8 baytlık bir tanımlayıcı başlık yazılır. Başlığı yazmaktan kaçınmak için bir `Serializer` oluşturun ve bunu `serialize`'a ilk argüman olarak kullanın. Ayrıca bkz. [`Serialization.writeheader`](@ref).

Veri formatı, küçük (1.x) Julia sürümlerinde değişebilir, ancak önceki 1.x sürümleriyle yazılan dosyalar okunabilir kalacaktır. Bunun ana istisnası, bir dış paketteki bir türün tanımının değişmesidir. Bu durumda, etkilenen paketin uyumlu bir sürümünü ortamınıza açıkça belirtmek gerekebilir. Paketler içindeki özel işlevlerin bile yeniden adlandırılması, mevcut dosyaların senkronizasyonunu bozabilir. Anonim işlevler özel bir dikkat gerektirir: çünkü adları otomatik olarak oluşturulur, küçük kod değişiklikleri onların yeniden adlandırılmasına neden olabilir. Uzun vadeli depolama için tasarlanmış dosyalarda anonim işlevlerin serileştirilmesinden kaçınılmalıdır.

Bazı durumlarda, okuma ve yazma makinelerinin kelime boyutu (32 veya 64 bit) eşleşmelidir. Daha nadir durumlarda, işletim sistemi veya mimari de eşleşmelidir; örneğin, platforma bağımlı kod içeren paketler kullanıldığında.
