```
mktempdir(parent=tempdir(); prefix="jl_", cleanup=true) -> path
```

`parent` dizininde, verilen `prefix` ve rastgele bir ek ile oluşturulmuş bir isimle geçici bir dizin oluşturur ve yolunu döner. Ayrıca, bazı platformlarda, `prefix` içindeki herhangi bir son `'X'` karakteri rastgele karakterlerle değiştirilebilir. Eğer `parent` mevcut değilse, bir hata fırlatır. `cleanup` seçeneği, geçici dizinin işlemin çıkışında otomatik olarak silinip silinmeyeceğini kontrol eder.

!!! compat "Julia 1.2"
    `prefix` anahtar argümanı Julia 1.2'de eklendi.


!!! compat "Julia 1.3"
    `cleanup` anahtar argümanı Julia 1.3'te eklendi. İlgili olarak, 1.3'ten itibaren, Julia, `mktempdir` ile oluşturulan geçici yolları, `cleanup` açıkça `false` olarak ayarlanmamışsa, Julia işlemi çıkarken silecektir.


Ayrıca bakınız: [`mktemp`](@ref), [`mkdir`](@ref).
