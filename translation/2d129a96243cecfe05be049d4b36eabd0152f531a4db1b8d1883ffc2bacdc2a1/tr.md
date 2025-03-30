```
finish(ts::AbstractTestSet)
```

Verilen test seti için gerekli son işlemleri yapar. Bu, bir test bloğu çalıştıktan sonra `@testset` altyapısı tarafından çağrılır.

Özel `AbstractTestSet` alt türleri, kendilerini test sonuçları ağacına eklemek için ebeveynlerine (varsa) `record` çağırmalıdır. Bu şu şekilde uygulanabilir:

```julia
if get_testset_depth() != 0
    # Bu test setini ebeveyn test setine ekle
    parent_ts = get_testset()
    record(parent_ts, self)
    return self
end
```
