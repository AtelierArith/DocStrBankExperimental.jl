```
FILE(::Ptr)
FILE(::IO)
```

A libc `FILE*`, açılmış bir dosyayı temsil eder.

[`ccall`](@ref) için bir `Ptr{FILE}` argümanı olarak geçirilebilir ve ayrıca [`seek`](@ref), [`position`](@ref) ve [`close`](@ref) destekler.

Bir `FILE`, sıradan bir `IO` nesnesinden oluşturulabilir, sağlanan dosya açık olmalıdır. Daha sonra kapatılmalıdır.

# Örnekler

```jldoctest
julia> using Base.Libc

julia> mktemp() do _, io
           # libc'den `puts(char*, FILE*)` kullanarak geçici dosyaya yaz
           file = FILE(io)
           ccall(:fputs, Cint, (Cstring, Ptr{FILE}), "hello world", file)
           close(file)
           # dosyayı tekrar oku
           seek(io, 0)
           read(io, String)
       end
"hello world"
```
