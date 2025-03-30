```
lowrankupdowndate!(F::CHOLMOD.Factor, C::Sparse, update::Cint)
```

Bir `LDLt` veya `LLt` Faktörizasyonu `F`'yi `A ± C*C'` faktörizasyonuna güncelleyin.

Eğer seyrekliği koruyan faktörizasyon kullanılıyorsa, yani `L*L' == P*A*P'` ise yeni faktör `L*L' == P*A*P' + C'*C` olacaktır.

`update`: `Cint(1)` için `A + CC'`, `Cint(0)` için `A - CC'`
