```
sprint(f::Function, args...; context=nothing, sizehint=0)
```

Verilen fonksiyonu bir I/O akışı ile ve sağlanan ek argümanlarla çağırır. Bu I/O akışına yazılan her şey bir dize olarak döndürülür. `context`, özelliklerinin kullanılacağı bir [`IOContext`](@ref) olabilir, bir özelliği ve değerini belirten bir `Pair`, veya birden fazla özelliği ve değerlerini belirten `Pair`'lerin bir demeti olabilir. `sizehint`, tamponun kapasitesini (bayt cinsinden) önerir.

İsteğe bağlı anahtar argümanı `context`, bir `:key=>value` çifti, bir `:key=>value` çiftleri demeti veya `f`'ye geçirilen I/O akışı için kullanılan özellikleri olan bir `IO` veya [`IOContext`](@ref) nesnesi olarak ayarlanabilir. İsteğe bağlı `sizehint`, dizeyi yazmak için kullanılan tampon için ayrılması önerilen boyuttur (bayt cinsinden).

!!! compat "Julia 1.7"
    Anahtar `context`'e bir demet geçmek, Julia 1.7 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> sprint(show, 66.66666; context=:compact => true)
"66.6667"

julia> sprint(showerror, BoundsError([1], 100))
"BoundsError: attempt to access 1-element Vector{Int64} at index [100]"
```
