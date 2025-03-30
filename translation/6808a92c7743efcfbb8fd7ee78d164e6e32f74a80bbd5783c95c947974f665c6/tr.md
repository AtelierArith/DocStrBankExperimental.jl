```
Modül
```

Bir `Modül`, ayrı bir global değişken çalışma alanıdır. Ayrıntılar için [`modül`](@ref) ve [modüller hakkında kılavuz bölümü](@ref modules) bakınız.

```
Module(name::Symbol=:anonymous, std_imports=true, default_names=true)
```

Belirtilen isimle bir modül döndürür. Bir `baremodule`, `Module(:ModuleName, false)` ile karşılık gelir.

Hiçbir isim içermeyen boş bir modül, `Module(:ModuleName, false, false)` ile oluşturulabilir. Bu modül `Base` veya `Core`'u içermeyecek ve kendisine bir referans içermeyecektir.
