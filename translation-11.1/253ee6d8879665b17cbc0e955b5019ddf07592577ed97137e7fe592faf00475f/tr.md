```
readlines(io::IO=stdin; keep::Bool=false)
readlines(filename::AbstractString; keep::Bool=false)
```

Bir I/O akışının veya bir dosyanın tüm satırlarını bir dize vektörü olarak okuyun. Davranış, [`readline`](@ref) fonksiyonunu aynı argümanlarla tekrar tekrar çağırmanın sonucunu kaydetmek ve elde edilen satırları bir dize vektörü olarak saklamakla eşdeğerdir. Tüm satırları bir kerede okumadan satırları yinelemek için [`eachline`](@ref) fonksiyonuna da bakın.

# Örnekler

```jldoctest
julia> write("my_file.txt", "JuliaLang bir GitHub organizasyonudur.\nBirçok üyesi vardır.\n");

julia> readlines("my_file.txt")
2-element Vector{String}:
 "JuliaLang bir GitHub organizasyonudur."
 "Birçok üyesi vardır."

julia> readlines("my_file.txt", keep=true)
2-element Vector{String}:
 "JuliaLang bir GitHub organizasyonudur.\n"
 "Birçok üyesi vardır.\n"

julia> rm("my_file.txt")
```
