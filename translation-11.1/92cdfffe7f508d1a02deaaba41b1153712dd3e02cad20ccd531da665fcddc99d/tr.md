```
Base.hasfastin(T)
```

`collection::T` içinde `x ∈ collection` hesaplamasının "hızlı" bir işlem olarak kabul edilip edilemeyeceğini belirleyin (tipik olarak sabit veya logaritmik karmaşıklık). `hasfastin(x) = hasfastin(typeof(x))` tanımı, örneklerin türler yerine geçebilmesi için kolaylık sağlamak amacıyla verilmiştir. Ancak, tür argümanı kabul eden form yeni türler için tanımlanmalıdır.

`hasfastin(T)` için varsayılan değer, [`AbstractSet`](@ref), [`AbstractDict`](@ref) ve [`AbstractRange`](@ref) alt türleri için `true` ve aksi takdirde `false`'dır.
