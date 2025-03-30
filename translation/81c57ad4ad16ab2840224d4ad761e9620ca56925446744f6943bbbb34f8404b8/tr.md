```
Base.depwarn(msg::String, funcsym::Symbol; force=false)
```

`msg`'yi bir deprecasyon uyarısı olarak yazdırır. `funcsym` sembolü, çağıran fonksiyonun adını temsil eder ve deprecasyon uyarısının her çağrı yerinde yalnızca ilk kez yazdırılmasını sağlamak için kullanılır. Uyarının her zaman gösterilmesini istiyorsanız `force=true` olarak ayarlayın, bu durumda Julia `--depwarn=no` ile başlatılmış olsa bile (varsayılan) uyarı her zaman gösterilecektir.

Ayrıca [`@deprecate`](@ref) bakınız.

# Örnekler

```julia
function deprecated_func()
    Base.depwarn("Don't use `deprecated_func()`!", :deprecated_func)

    1 + 1
end
```
