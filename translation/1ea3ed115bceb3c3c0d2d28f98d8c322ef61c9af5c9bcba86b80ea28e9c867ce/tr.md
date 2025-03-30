```
code_warntype([io::IO], f, types; debuginfo=:default)
```

Verilen genel işlev ve `io` için tür imzasına uyan yöntemler için düşürülmüş ve tür çıkarılmış AST'leri yazdırır; varsayılan olarak `stdout`'a. AST'ler, performans için sorunlu olabilecek "non-leaf" türlerin vurgulanacak şekilde anotasyonlanmıştır (renk mevcutsa, kırmızı olarak gösterilir). Bu, potansiyel tür istikrarsızlığına dair bir uyarı olarak hizmet eder.

Tüm non-leaf türler performans açısından özellikle sorunlu değildir ve belirli bir türün performans özellikleri derleyicinin bir uygulama ayrıntısıdır. `code_warntype`, performans kaygısı olabilecek türleri kırmızı renkle vurgulama konusunda temkinli davranır, bu nedenle bazı türler performansı etkilemese bile kırmızı renkle vurgulanabilir. Somut türlerin küçük birleşimleri genellikle bir sorun değildir, bu nedenle bunlar sarı renkle vurgulanır.

Anahtar argüman `debuginfo`, kod yorumlarının ayrıntı seviyesini belirtmek için `:source` veya `:none` (varsayılan) değerlerinden biri olabilir.

Daha fazla bilgi için kılavuzun Performans İpuçları sayfasındaki [`@code_warntype`](@ref) bölümüne bakın.

Ayrıca: [`@code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref), [`code_native`](@ref).
