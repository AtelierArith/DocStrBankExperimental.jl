```
realpath(path::AbstractString) -> String
```

Bir yolu sembolik bağlantıları genişleterek ve "." ve ".." girişlerini kaldırarak standart hale getirir. Büyük/küçük harf duyarsız ve büyük/küçük harf koruyan dosya sistemlerinde (tipik olarak Mac ve Windows), yolun dosya sisteminde saklanan büyük/küçük harf durumu döndürülür.

(Bu işlev, `path` dosya sisteminde mevcut değilse bir istisna fırlatır.)
