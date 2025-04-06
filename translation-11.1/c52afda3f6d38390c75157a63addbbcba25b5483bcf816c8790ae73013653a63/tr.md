```
similar(A::AbstractSparseMatrixCSC{Tv,Ti}, [::Type{TvNew}, ::Type{TiNew}, m::Integer, n::Integer]) where {Tv,Ti}
```

Verilen kaynak `SparseMatrixCSC`'ye dayanarak, belirtilen eleman türü, indeks türü ve boyut ile başlatılmamış bir değiştirilebilir dizi oluşturur. Yeni seyrek matris, orijinal seyrek matrisin yapısını korur, yalnızca çıkış matrisinin boyutları çıkıştan farklı olduğunda durum farklıdır.

Çıkış matrisinin, girdi ile aynı konumlarda sıfırları vardır, ancak sıfır olmayan konumlar için başlatılmamış değerler içerir.
