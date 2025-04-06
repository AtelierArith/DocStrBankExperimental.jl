```
CachingPool(workers::Vector{Int})
```

`AbstractWorkerPool`'un bir uygulaması. [`remote`](@ref), [`remotecall_fetch`](@ref), [`pmap`](@ref) (ve uzaktan işlevleri uzaktan çalıştıran diğer çağrılar) işçi düğümlerinde serileştirilmiş/serileştirilmemiş işlevlerin önbelleğe alınmasından faydalanır, özellikle büyük miktarda veri yakalayabilen kapanışlar için.

Uzaktan önbellek, döndürülen `CachingPool` nesnesinin ömrü boyunca korunur. Önbelleği daha erken temizlemek için `clear!(pool)` kullanın.

Küresel değişkenler için, yalnızca bağlamalar bir kapanışta yakalanır, veri değil. Küresel verileri yakalamak için `let` blokları kullanılabilir.

# Örnekler

```julia
const foo = rand(10^8);
wp = CachingPool(workers())
let foo = foo
    pmap(i -> sum(foo) + i, wp, 1:100);
end
```

Yukarıdaki kod, `foo`'yu her işçiye yalnızca bir kez aktarır.
