```
read(filename::AbstractString)
```

Bir dosyanın tüm içeriğini `Vector{UInt8}` olarak oku.

```
read(filename::AbstractString, String)
```

Bir dosyanın tüm içeriğini bir dize olarak oku.

```
read(filename::AbstractString, args...)
```

Bir dosyayı aç ve içeriğini oku. `args`, `read` fonksiyonuna iletilir: bu, `open(io->read(io, args...), filename)` ile eşdeğerdir.
