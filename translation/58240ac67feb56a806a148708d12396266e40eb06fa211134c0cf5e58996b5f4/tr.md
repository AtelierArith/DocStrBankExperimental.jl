```
setglobalonce!(module::Module, name::Symbol, value,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Daha önce ayarlanmamışsa, bir globali belirli bir değere ayarlamak için atomik olarak işlemleri gerçekleştirin.

!!! uyumluluk "Julia 1.11"
    Bu işlev Julia 1.11 veya daha yenisini gerektirir.


Ayrıca [`setpropertyonce!`](@ref Base.setpropertyonce!) ve [`setglobal!`](@ref) ile de bakabilirsiniz.
