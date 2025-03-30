```
copyline(out::IO, io::IO=stdin; keep::Bool=false)
copyline(out::IO, filename::AbstractString; keep::Bool=false)

Bir I/O `stream` veya bir dosyadan bir metin satırını `out` akışına kopyalar ve `out`'u döner.

Bir dosyadan okurken, metnin UTF-8 ile kodlandığı varsayılır. Girişteki satırlar `'\n'` veya `"\r\n"` ile veya bir giriş akışının sonu ile biter. `keep` false olduğunda (varsayılan olarak olduğu gibi), bu son satır sonu karakterleri döndürülmeden önce satırdan kaldırılır. `keep` true olduğunda, bunlar satırın bir parçası olarak döndürülür.

[`readline`](@ref) ile benzer, bu `String` döndürür; aksine, `copyline` doğrudan `out`'a yazar, bir dize tahsis etmeden. (Bu, örneğin, verileri önceden tahsis edilmiş bir [`IOBuffer`](@ref) içine okumak için kullanılabilir.)

Daha genel ayırıcılar için okumak üzere [`copyuntil`](@ref) ile de bakabilirsiniz.

# Örnekler

```

jldoctest julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyline(IOBuffer(), "my_file.txt"))) "JuliaLang is a GitHub organization."

julia> String(take!(copyline(IOBuffer(), "my_file.txt", keep=true))) "JuliaLang is a GitHub organization.\n"

julia> rm("my_file.txt") ```
