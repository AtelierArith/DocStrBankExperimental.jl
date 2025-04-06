```
readline(io::IO=stdin; keep::Bool=false)
readline(filename::AbstractString; keep::Bool=false)
```

Verilen I/O akışından veya dosyadan (varsayılan olarak `stdin`) bir satır metin okuyun. Bir dosyadan okurken, metnin UTF-8 ile kodlandığı varsayılır. Girişteki satırlar `'\n'` veya `"\r\n"` ile veya bir giriş akışının sonu ile biter. `keep` false olduğunda (varsayılan olarak olduğu gibi), bu sonlandırıcı yeni satır karakterleri, döndürülen satırdan önce kaldırılır. `keep` true olduğunda, bunlar satırın bir parçası olarak döndürülür.

Bir `String` döndürür. Bunun yerine başka bir akışa yerinde yazmak için [`copyline`](@ref) ile de bakın (bu, önceden tahsis edilmiş bir [`IOBuffer`](@ref) olabilir).

Daha genel ayırıcılar için okumak üzere [`readuntil`](@ref) ile de bakın.

# Örnekler

```jldoctest
julia> write("my_file.txt", "JuliaLang bir GitHub organizasyonudur.\nBirçok üyesi vardır.\n");

julia> readline("my_file.txt")
"JuliaLang bir GitHub organizasyonudur."

julia> readline("my_file.txt", keep=true)
"JuliaLang bir GitHub organizasyonudur.\n"

julia> rm("my_file.txt")
```

```julia-repl
julia> print("Adınızı girin: ")
Adınızı girin:

julia> your_name = readline()
Logan
"Logan"
```
