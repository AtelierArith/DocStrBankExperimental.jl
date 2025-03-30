```
AtomicMemory{T} == GenericMemory{:atomic, T, Core.CPU}
```

Sabit boyutlu [`DenseVector{T}`](@ref DenseVector). Elemanlarına erişim atomik olarak gerçekleştirilir (`:monotonic` sıralaması ile). Elemanlardan herhangi birinin ayarlanması `@atomic` makrosu kullanılarak ve sıralamanın açıkça belirtilmesiyle gerçekleştirilmelidir.

!!! warning
    Her bir eleman erişildiğinde bağımsız olarak atomiktir ve atomik olmayan bir şekilde ayarlanamaz. Şu anda `@atomic` makrosu ve daha yüksek seviyeli arayüz tamamlanmamıştır, ancak gelecekteki bir uygulama için yapı taşları içsel intrinziklerdir: `Core.memoryrefget`, `Core.memoryrefset!`, `Core.memoryref_isassigned`, `Core.memoryrefswap!`, `Core.memoryrefmodify!` ve `Core.memoryrefreplace!`.


Detaylar için [Atomic Operations](@ref man-atomic-operations) sayfasına bakın.

!!! compat "Julia 1.11"
    Bu tür, Julia 1.11 veya daha yenisini gerektirir.

