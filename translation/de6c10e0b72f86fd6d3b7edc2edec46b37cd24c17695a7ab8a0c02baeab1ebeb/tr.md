```
write(io::IO, x)
```

Verilen I/O akışına veya dosyasına bir değerin kanonik ikili temsilini yazın. Akışa yazılan byte sayısını döndürün. Metin temsilini yazmak için [`print`](@ref) fonksiyonuna da bakın (kodlama `io`ya bağlı olabilir).

Yazılan değerin endianlığı, ana sistemin endianlığına bağlıdır. Yazarken/okurken sabit bir endianlığa dönüştürmek için (örneğin, [`htol`](@ref) ve [`ltoh`](@ref) kullanarak) platformlar arasında tutarlı sonuçlar elde edebilirsiniz.

Aynı `write` çağrısıyla birden fazla değer yazabilirsiniz. Yani, aşağıdakiler eşdeğerdir:

```
write(io, x, y...)
write(io, x) + write(io, y...)
```

# Örnekler

Tutarlı serileştirme:

```jldoctest
julia> fname = tempname(); # rastgele geçici dosya adı

julia> open(fname,"w") do f
           # 64bit tam sayıyı küçük endian byte sırasına yazdığımızdan emin olun
           write(f,htol(Int64(42)))
       end
8

julia> open(fname,"r") do f
           # Ana byte sırasına ve ana tam sayı türüne geri dönüştür
           Int(ltoh(read(f,Int64)))
       end
42
```

Yazma çağrılarını birleştirme:

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang bir GitHub organizasyonudur.", " Birçok üyesi var.")
56

julia> String(take!(io))
"JuliaLang bir GitHub organizasyonudur. Birçok üyesi var."

julia> write(io, "Bazen o üyeler") + write(io, " belge yazar.")
44

julia> String(take!(io))
"Bazen o üyeler belge yazar."
```

`write` yöntemleri olmayan kullanıcı tanımlı düz veri türleri, bir `Ref` içinde sarıldığında yazılabilir:

```jldoctest
julia> struct MyStruct; x::Float64; end

julia> io = IOBuffer()
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=Inf, ptr=1, mark=-1)

julia> write(io, Ref(MyStruct(42.0)))
8

julia> seekstart(io); read!(io, Ref(MyStruct(NaN)))
Base.RefValue{MyStruct}(MyStruct(42.0))
```
