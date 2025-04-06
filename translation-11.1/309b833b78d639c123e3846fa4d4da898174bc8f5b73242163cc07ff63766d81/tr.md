```
record(ts::AbstractTestSet, res::Result)
```

Bir sonucu bir test setine kaydedin. Bu işlev, her seferinde bir `@test` makrosu tamamlandığında `@testset` altyapısı tarafından çağrılır ve test sonucunu (bir `Error` olabilir) alır. Ayrıca, test bloğu içinde ancak bir `@test` bağlamının dışında bir istisna fırlatıldığında bir `Error` ile de çağrılacaktır.
