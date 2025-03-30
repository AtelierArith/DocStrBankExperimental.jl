```
upstream(ref::GitReference) -> Union{GitReference, Nothing}
```

`ref` içeren dalın belirli bir yukarı akış dalı olup olmadığını belirleyin.

Eğer varsa yukarı akış dalına bir `GitReference` döndürün, aksi takdirde istenen dalın yukarı akış karşılığı yoksa [`nothing`](@ref) döndürün.
