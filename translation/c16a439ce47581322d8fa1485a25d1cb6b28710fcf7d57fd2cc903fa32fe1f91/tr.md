```
display(x)
display(d::AbstractDisplay, x)
display(mime, x)
display(d::AbstractDisplay, mime, x)
```

`x`'i, genellikle `x` için en zengin desteklenen multimedya çıktısını kullanarak, görüntüleme yığınındaki en üstteki uygun görüntüleme ile gösterin; düz metin [`stdout`](@ref) çıktısı bir yedek olarak kullanılır. `display(d, x)` varyantı, yalnızca verilen görüntüleme `d` üzerinde `x`'i görüntülemeye çalışır ve `d` bu tür nesneleri görüntüleyemiyorsa bir [`MethodError`](@ref) fırlatır.

Genel olarak, `display` çıktısının `stdout`'a gideceğini varsayamazsınız ([`print(x)`](@ref) veya [`show(x)`](@ref) ile karşılaştırıldığında). Örneğin, `display(x)` bir görüntü ile ayrı bir pencere açabilir. `display(x)`, "şu anda mevcut çıktı cihaz(lar)ı için `x`'i en iyi şekilde göster" anlamına gelir. `stdout`'a gitmesi garanti edilen REPL benzeri metin çıktısı istiyorsanız, bunun yerine [`show(stdout, "text/plain", x)`](@ref) kullanın.

Ayrıca, yalnızca istenen MIME türünü kullanarak `x`'i görüntülemeye çalışan iki varyant vardır (örneğin, `"image/png"` gibi bir MIME türü dizesi), bu tür desteklenmiyorsa görüntüleme(ler) veya `x` için bir `MethodError` fırlatır. Bu varyantlarla, istenen MIME türünde "ham" veriyi sağlamak için `x::AbstractString` (metin tabanlı depolama için MIME türleri, örneğin text/html veya application/postscript) veya `x::Vector{UInt8}` (ikili MIME türleri için) geçirebilirsiniz.

Bir türün örneklerinin nasıl görüntüleneceğini özelleştirmek için, [`show`](@ref) yerine `display`'i aşırı yükleyin; bu, [özel güzel yazdırma](@ref man-custom-pretty-printing) konusundaki kılavuzda açıklanmıştır.
