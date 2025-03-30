```
modifyproperty!(x, f::Symbol, op, v, order::Symbol=:not_atomic)
```

`@atomic op(x.f, v)` (ve onun eşdeğeri `@atomic x.f op v`) ifadesi `modifyproperty!(x, :f, op, v, :sequentially_consistent)` döndürür; burada ilk argüman bir `getproperty` ifadesi olmalı ve atomik olarak değiştirilir.

`op(getproperty(x, f), v)` çağrısı, varsayılan olarak `x` nesnesinin `f` alanında saklanabilecek bir değer döndürmelidir. Özellikle, [`setproperty!`](@ref Base.setproperty!)'in varsayılan davranışının aksine, `convert` fonksiyonu otomatik olarak çağrılmaz.

Ayrıca [`modifyfield!`](@ref Core.modifyfield!) ve [`setproperty!`](@ref Base.setproperty!)'e de bakın.
