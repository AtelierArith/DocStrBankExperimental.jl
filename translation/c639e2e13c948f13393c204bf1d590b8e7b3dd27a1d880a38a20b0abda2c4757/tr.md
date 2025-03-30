```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

Bir I/O `stream` veya bir dosyadan, verilen ayırıcıya kadar bir dize okuyun. Ayırıcı bir `UInt8`, `AbstractChar`, dize veya vektör olabilir. Anahtar argüman `keep`, ayırıcının sonucun içinde yer alıp almayacağını kontrol eder. Metnin UTF-8 ile kodlandığı varsayılmaktadır.

Eğer `delim` bir `AbstractChar` veya bir dize ise bir `String` döndürün, aksi takdirde `Vector{typeof(delim)}` döndürün. Bunun yanı sıra, başka bir akışa (önceden tahsis edilmiş bir [`IOBuffer`](@ref) olabilir) yerinde yazmak için [`copyuntil`](@ref) fonksiyonuna da bakın.

# Örnekler

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
