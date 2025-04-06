```
tonext(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

`dt`'yi `dow` ile ilgili olan bir sonraki haftanın gününe ayarlar; burada `1 = Pazartesi, 2 = Salı, vb.` `same=true` olarak ayarlandığında, mevcut `dt`'nin bir sonraki `dow` olarak kabul edilmesine izin verir ve ayarlama yapılmaz.
