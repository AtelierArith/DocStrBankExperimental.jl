```
set_zero_subnormals(yes::Bool) -> Bool
```

Eğer `yes` `false` ise, sonraki kayan nokta işlemleri alt normal değerler ("denormals") için IEEE aritmetiği kurallarını takip eder. Aksi takdirde, kayan nokta işlemleri alt normal girişleri veya çıkışları sıfıra dönüştürmek için izin verilir (ancak zorunlu değildir). `true` döner, eğer `yes==true` ise ama donanım alt normal sayıları sıfırlamayı desteklemiyorsa.

`set_zero_subnormals(true)` bazı donanımlarda bazı hesaplamaları hızlandırabilir. Ancak, `(x-y==0) == (x==y)` gibi kimlikleri bozabilir.

!!! uyarı     Bu fonksiyon yalnızca mevcut iş parçacığını etkiler.
