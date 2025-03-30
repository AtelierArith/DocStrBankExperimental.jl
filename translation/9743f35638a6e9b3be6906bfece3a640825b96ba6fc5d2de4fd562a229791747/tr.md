```
prevfloat(x::AbstractFloat, n::Integer)
```

`x`'e `n` kez ardışık `prevfloat` uygulamalarının sonucu, eğer `n >= 0` ise; `n < 0` ise [`nextfloat`](@ref) uygulamalarının `-n` kez sonucudur.
