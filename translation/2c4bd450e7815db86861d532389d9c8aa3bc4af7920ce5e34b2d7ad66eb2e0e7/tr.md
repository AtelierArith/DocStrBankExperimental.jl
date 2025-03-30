```
remote_do(f, id::Integer, args...; kwargs...) -> nothing
```

`f`'yi işçi `id` üzerinde asenkron olarak çalıştırır. [`remotecall`](@ref) ile karşılaştırıldığında, hesaplamanın sonucunu saklamaz ve tamamlanmasını beklemenin bir yolu yoktur.

Başarılı bir çağrı, isteğin uzak düğümde yürütülmek üzere kabul edildiğini gösterir.

Aynı işçiye yapılan ardışık `remotecall`'lar, çağrıldıkları sırayla sıralanırken, uzak işçi üzerindeki yürütme sırası belirsizdir. Örneğin, `remote_do(f1, 2); remotecall(f2, 2); remote_do(f3, 2)` çağrısı `f1`'e yapılan çağrıyı sıralar, ardından `f2` ve `f3`'ü bu sırayla sıralar. Ancak, `f1`'in işçi 2 üzerinde `f3`'ten önce yürütüleceği garanti edilmez.

`f` tarafından fırlatılan herhangi bir istisna, uzak işçi üzerinde [`stderr`](@ref) üzerine yazdırılır.

Anahtar argümanlar, varsa, `f`'ye iletilir.
