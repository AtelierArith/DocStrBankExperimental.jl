```
deserialize(stream)
```

[`serialize`](@ref) ile yazılmış bir değeri okuyun. `deserialize`, `stream`'den okunan ikili verinin doğru olduğunu ve [`serialize`](@ref) ile uyumlu bir uygulama tarafından serileştirildiğini varsayar. `deserialize`, basitlik ve performans için tasarlanmıştır, bu nedenle okunan veriyi doğrulamaz. Bozuk veriler işlem sonlanmasına neden olabilir. Çağrıcı, `stream`'den okunan verinin bütünlüğünü ve doğruluğunu sağlamalıdır.
