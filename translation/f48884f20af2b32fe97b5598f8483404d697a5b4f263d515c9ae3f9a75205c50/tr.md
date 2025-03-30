```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

Profiling sonuçlarını `io`'ya yazdırır. Bu varyant, daha önceki bir [`retrieve`](@ref) çağrısı ile dışa aktarılan sonuçları incelemek için kullanılır. Geri izlemelerin `data` vektörünü ve satır bilgileri için bir `lidict` sözlüğünü sağlayın.

Geçerli anahtar kelime argümanlarının açıklaması için `Profile.print([io], data)`'ya bakın.
