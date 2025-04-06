```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

`path` için mevcut dizinden veya isteğe bağlı bir başlangıç dizininden bir göreli dosya yolu döndürür. Bu bir yol hesaplamasıdır: `path` veya `startpath`'in varlığını veya doğasını doğrulamak için dosya sistemine erişilmez.

Windows'ta, yolun her parçasına, sürücü harfleri hariç, büyük/küçük harf duyarlılığı uygulanır. Eğer `path` ve `startpath` farklı sürücüleri işaret ediyorsa, `path`'in mutlak yolu döndürülür.
