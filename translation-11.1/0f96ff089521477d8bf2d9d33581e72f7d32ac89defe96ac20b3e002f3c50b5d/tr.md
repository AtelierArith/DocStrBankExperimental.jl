```
Serialization.writeheader(s::AbstractSerializer)
```

Belirtilen serileştiriciye tanımlayıcı bir başlık yazın. Başlık, aşağıdaki gibi 8 bayttan oluşur:

| Ofset | Açıklama                                          |
|:----- |:------------------------------------------------- |
| 0     | etiket baytı (0x37)                               |
| 1-2   | imza baytları "JL"                                |
| 3     | protokol versiyonu                                |
| 4     | bit 0-1: sonlandırma sırası: 0 = küçük, 1 = büyük |
| 4     | bit 2-3: platform: 0 = 32-bit, 1 = 64-bit         |
| 5-7   | ayrılmış                                          |
