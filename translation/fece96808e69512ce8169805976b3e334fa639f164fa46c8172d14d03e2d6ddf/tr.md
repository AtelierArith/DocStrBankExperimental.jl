```
ParserError
```

[`tryparse`](@ref) ve [`tryparsefile`](@ref) işleme başarısız olduğunda döndürülen tür. Aşağıdakiler de dahil olmak üzere bazı alanları içerir:

  * `pos`, hatanın meydana geldiği sıradaki konum
  * `table`, şu ana kadar başarıyla ayrıştırılan sonuç
  * `type`, farklı hata türleri için farklı bir hata türü
