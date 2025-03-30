```
pushdisplay(d::AbstractDisplay)
```

Yeni bir `d` görüntüsünü global görüntü arka planı yığınına ekler. `display(x)` veya `display(mime, x)` çağrısı, yığındaki en üstteki uyumlu arka planda `x`'i görüntüler (yani, [`MethodError`](@ref) fırlatmayan en üstteki arka plan).
