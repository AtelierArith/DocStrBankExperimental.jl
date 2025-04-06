```
writeline(buf::IO, m::AbstractMenu, idx::Int, iscursor::Bool)
```

`idx` indeksindeki seçeneği `buf`'a yazın. `iscursor` `true` ise, bu öğenin mevcut imleç konumunda olduğunu (yani "Enter" tuşuna basarak seçilecek olan) belirtir.

Eğer `m` bir `ConfiguredMenu` ise, `TerminalMenus` imleç göstergesini yazdıracaktır. Aksi takdirde, çağrılan fonksiyonun bu yazdırmayı yönetmesi beklenir.

!!! compat "Julia 1.6"
    `writeline` Julia 1.6 veya daha yüksek bir sürüm gerektirir.

    Daha eski Julia sürümlerinde, bu `writeLine(buf::IO, m::AbstractMenu, idx, iscursor::Bool)` idi ve `m`'nin yapılandırılmamış olduğu varsayılır. Seçim ve imleç göstergeleri `TerminalMenus.CONFIG`'den elde edilebilir.

    Bu eski fonksiyon, tüm Julia 1.x sürümlerinde desteklenmektedir ancak Julia 2.0'da kaldırılacaktır.

