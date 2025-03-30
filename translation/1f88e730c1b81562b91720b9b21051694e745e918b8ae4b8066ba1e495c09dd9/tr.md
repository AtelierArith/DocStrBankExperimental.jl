```
setpropertyonce!(x, f::Symbol, value, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Daha önce ayarlanmamışsa `x.f`'yi `value` olarak ayarlamak için bir karşılaştırma-değiştirme işlemi gerçekleştirin. `@atomiconce x.f = value` sözdizimi, işlev çağrısı biçimi yerine kullanılabilir.

Ayrıca [`setfieldonce!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`replaceproperty!`](@ref Base.replaceproperty!) bakınız.

!!! compat "Julia 1.11"
    Bu işlev Julia 1.11 veya daha yenisini gerektirir.

