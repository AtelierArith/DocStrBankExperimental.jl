```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Bir globalı belirli bir değere almak ve koşullu olarak ayarlamak için atomik olarak işlemleri gerçekleştirin.

!!! uyumluluk "Julia 1.11"
    Bu işlev Julia 1.11 veya daha yenisini gerektirir.


Ayrıca [`replaceproperty!`](@ref Base.replaceproperty!) ve [`setglobal!`](@ref) ile de bakabilirsiniz.
