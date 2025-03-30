```
@lock l expr
```

`lock(f, l::AbstractLock)` makrosunun `f` fonksiyonu yerine `expr` ile versiyonudur. Aşağıdakine genişler:

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

Bu, [`lock`](@ref) kullanarak bir `do` bloğu ile benzer, ancak bir kapanış oluşturmaktan kaçınır ve böylece performansı artırabilir.

!!! uyumluluk
    `@lock`, Julia 1.3'te eklendi ve Julia 1.10'da dışa aktarıldı.

