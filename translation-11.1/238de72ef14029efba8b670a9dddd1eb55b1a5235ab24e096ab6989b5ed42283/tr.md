```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

Yeni bir dizin oluşturun `path` adıyla ve izinlerle `mode`. `mode` varsayılan olarak `0o777`'dir ve mevcut dosya oluşturma maskesi tarafından değiştirilir. Bu işlev asla birden fazla dizin oluşturmaz. Eğer dizin zaten mevcutsa veya bazı ara dizinler mevcut değilse, bu işlev bir hata fırlatır. Gerekli tüm ara dizinleri oluşturan bir işlev için [`mkpath`](@ref) kısmına bakın. `path` döndürülür.

# Örnekler

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
