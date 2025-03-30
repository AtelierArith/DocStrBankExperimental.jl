```
copyuntil(out::IO, stream::IO, delim; keep::Bool = false)
copyuntil(out::IO, filename::AbstractString, delim; keep::Bool = false)

Bir I/O `stream` veya bir dosyadan, verilen ayırıcıya kadar bir dizeyi `out` akışına kopyalar ve `out`'u döner. Ayırıcı bir `UInt8`, `AbstractChar`, dize veya vektör olabilir. Anahtar kelime argümanı `keep`, ayırıcının sonuca dahil edilip edilmeyeceğini kontrol eder. Metnin UTF-8 olarak kodlandığı varsayılmaktadır.

[`readuntil`](@ref) ile benzer; bu, bir `String` döner; aksine, `copyuntil` doğrudan `out`'a yazar, bir dize tahsis etmeden. (Bu, örneğin, önceden tahsis edilmiş bir [`IOBuffer`](@ref) içine veri okumak için kullanılabilir.)

# Örnekler

```

jldoctest julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", 'L'))) "Julia"

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", '.', keep = true))) "JuliaLang is a GitHub organization."

julia> rm("my_file.txt") ```
