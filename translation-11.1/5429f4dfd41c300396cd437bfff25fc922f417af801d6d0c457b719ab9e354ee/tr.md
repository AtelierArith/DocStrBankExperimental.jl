```
WeakRef(x)
```

`w = WeakRef(x)` Julia değeri `x` için bir [zayıf referans](https://en.wikipedia.org/wiki/Weak_reference) oluşturur: `w`, `x`'e bir referans içeriyor olsa da, `x`'in çöp toplayıcı tarafından toplanmasını engellemez. `w.value` ya `x`'dir (eğer `x` henüz çöp toplayıcı tarafından toplanmamışsa) ya da `nothing`dır (eğer `x` çöp toplayıcı tarafından toplanmışsa).

```jldoctest
julia> x = "a string"
"a string"

julia> w = WeakRef(x)
WeakRef("a string")

julia> GC.gc()

julia> w           # bir referans `x` aracılığıyla korunur
WeakRef("a string")

julia> x = nothing # referansı temizle

julia> GC.gc()

julia> w
WeakRef(nothing)
```
