```
nextfloat(x::AbstractFloat, n::Integer)
```

`x`'e `n` kez ardışık `nextfloat` uygulamasının sonucu, eğer `n >= 0` ise; `n < 0` ise [`prevfloat`](@ref) uygulamalarının `-n` kez sonucudur.
