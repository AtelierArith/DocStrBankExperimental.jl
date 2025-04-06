```
countlines(io::IO; eol::AbstractChar = '\n')
countlines(filename::AbstractString; eol::AbstractChar = '\n')

`io`'yu akış/dosya sonuna kadar okuyun ve satır sayısını sayın. Bir dosyayı belirtmek için dosya adını ilk argüman olarak geçirin. `'\n'` dışındaki EOL işaretleri, ikinci argüman olarak geçilerek desteklenir. `io`'nun son boş olmayan satırı, EOL ile bitmese bile sayılır; bu, [`eachline`](@ref) ve [`readlines`](@ref) tarafından döndürülen uzunlukla eşleşir.

Bir `String`'in satırlarını saymak için `countlines(IOBuffer(str))` kullanılabilir.

# Örnekler

```

jldoctest julia> io = IOBuffer("JuliaLang bir GitHub organizasyonudur.\n");

julia> countlines(io) 1

julia> io = IOBuffer("JuliaLang bir GitHub organizasyonudur.");

julia> countlines(io) 1

julia> eof(io) # satır sayma dosya işaretçisini hareket ettirir true

julia> io = IOBuffer("JuliaLang bir GitHub organizasyonudur.");

julia> countlines(io, eol = '.') 1

```

```

jldoctest julia> write("my_file.txt", "JuliaLang bir GitHub organizasyonudur.\n") 36

julia> countlines("my_file.txt") 1

julia> countlines("my_file.txt", eol = 'n') 4

julia> rm("my_file.txt")

```
