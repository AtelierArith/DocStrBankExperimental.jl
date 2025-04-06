```
show([io::IO = stdout], x)
```

Bir değer `x`'in metin temsilini çıkış akışı `io`'ya yazın. Yeni türler `T`, `show(io::IO, x::T)` ile aşırı yüklenmelidir. `show` tarafından kullanılan temsil genellikle Julia'ya özgü biçimlendirme ve tür bilgilerini içerir ve mümkün olduğunda ayrıştırılabilir Julia kodu olmalıdır.

[`repr`](@ref) `show`'un çıktısını bir dize olarak döndürür.

`T` türündeki nesneler için daha ayrıntılı insan tarafından okunabilir metin çıktısı almak için, ayrıca `show(io::IO, ::MIME"text/plain", ::T)` tanımlayın. Bu tür yöntemlerde `io`'nun `:compact` [`IOContext`](@ref) anahtarını kontrol etmek önerilir (genellikle `get(io, :compact, false)::Bool` olarak kontrol edilir), çünkü bazı konteynerler elemanlarını `:compact => true` ile bu yöntemle gösterir.

Ayrıca [`print`](@ref) ile ilgili, süssüz temsilleri yazar.

# Örnekler

```jldoctest
julia> show("Hello World!")
"Hello World!"
julia> print("Hello World!")
Hello World!
```
