```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

`x.f` üzerinde `expected`'dan `desired`'a bir karşılaştırma-değiştirme işlemi gerçekleştirin, egal'e göre. Fonksiyon çağrısı biçimi yerine `@atomicreplace x.f expected => desired` sözdizimi kullanılabilir.

Ayrıca bkz. [`replacefield!`](@ref Core.replacefield!) [`setproperty!`](@ref Base.setproperty!), [`setpropertyonce!`](@ref Base.setpropertyonce!).
