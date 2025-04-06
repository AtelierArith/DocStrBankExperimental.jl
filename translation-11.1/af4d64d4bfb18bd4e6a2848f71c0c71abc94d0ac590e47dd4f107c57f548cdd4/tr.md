```
LinearAlgebra.Givens(i1,i2,c,s) -> G
```

Bir Givens rotasyonu lineer operatörü. `c` ve `s` alanları, sırasıyla döndürme açısının kosinüsünü ve sinüsünü temsil eder. `Givens` türü, sol çarpma `G*A` ve konjuge transpoze sağ çarpma `A*G'` destekler. Bu türün bir `boyut`u yoktur ve bu nedenle `G*A` için `i2<=size(A,2)` veya `A*G'` için `i2<=size(A,1)` olduğu sürece, rastgele boyutlardaki matrislerle çarpılabilir.

Ayrıca bkz. [`givens`](@ref).
