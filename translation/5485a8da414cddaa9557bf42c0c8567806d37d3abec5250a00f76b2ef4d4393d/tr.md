```
repr(mime, x; context=nothing)
```

`x`'in istenen `mime` türünde temsilini içeren bir `AbstractString` veya `Vector{UInt8}` döndürür; bu, [`show(io, mime, x)`](@ref) tarafından yazıldığı gibi (uygun bir `show` mevcut değilse [`MethodError`](@ref) fırlatır). Metinsel temsillere sahip MIME türleri için (örneğin `"text/html"` veya `"application/postscript"` gibi) bir `AbstractString` dönerken, ikili veriler `Vector{UInt8}` olarak döner. (`istextmime(mime)` fonksiyonu, Julia'nın belirli bir `mime` türünü metin olarak değerlendirip değerlendirmediğini döndürür.)

İsteğe bağlı anahtar argümanı `context`, `show`'a geçirilen I/O akışı için kullanılan özellikleri olan `:key=>value` çifti veya bir `IO` veya [`IOContext`](@ref) nesnesi olarak ayarlanabilir.

Özel bir durum olarak, eğer `x` bir `AbstractString` (metinsel MIME türleri için) veya bir `Vector{UInt8}` (ikili MIME türleri için) ise, `repr` fonksiyonu `x`'in zaten istenen `mime` formatında olduğunu varsayar ve basitçe `x`'i döndürür. Bu özel durum `"text/plain"` MIME türüne uygulanmaz. Bu, ham verilerin `display(m::MIME, x)`'e geçirilmesi için yararlıdır.

Özellikle, `repr("text/plain", x)` genellikle insan tüketimi için tasarlanmış `x`'in "güzel basılmış" bir versiyonudur. Bunun yerine [`show(x)`](@ref) ile daha yakın bir şekilde `x`'in değerinin Julia'da nasıl girileceğine karşılık gelen bir dize döndürmek için [`repr(x)`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4];

julia> repr("text/plain", A)
"2×2 Matrix{Int64}:\n 1  2\n 3  4"
```
