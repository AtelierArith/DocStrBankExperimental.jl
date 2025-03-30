```
toprev(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

`dt`'yi `dow` ile ilgili önceki haftanın gününe ayarlar; burada `1 = Pazartesi, 2 = Salı, vb.` `same=true` olarak ayarlandığında, mevcut `dt` önceki `dow` olarak kabul edilir ve ayarlama yapılmaz.
