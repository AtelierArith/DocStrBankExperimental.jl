```
__init__
```

`__init__()` fonksiyonu bir modül yüklendiğinde çalışma zamanında *ilk kez* hemen yürütülür. Modüldeki diğer tüm ifadeler yürütüldükten sonra bir kez çağrılır. Modül tamamen yüklendikten sonra çağrıldığı için, alt modüllerin `__init__` fonksiyonları önce yürütülecektir. `__init__`'in iki tipik kullanımı, dış C kütüphanelerinin çalışma zamanı başlatma fonksiyonlarını çağırmak ve dış kütüphaneler tarafından döndürülen işaretçileri içeren global sabitleri başlatmaktır. Daha fazla ayrıntı için [modüller hakkında kılavuz bölümüne](@ref modules) bakın.

# Örnekler

```julia
const foo_data_ptr = Ref{Ptr{Cvoid}}(0)
function __init__()
    ccall((:foo_init, :libfoo), Cvoid, ())
    foo_data_ptr[] = ccall((:foo_data, :libfoo), Ptr{Cvoid}, ())
    nothing
end
```
