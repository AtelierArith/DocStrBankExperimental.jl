```
readdlm(source; options...)
```

Sütunların bir veya daha fazla boşlukla ayrıldığı varsayılmaktadır. Satır sonu ayırıcı olarak `\n` alınır. Tüm veriler sayısal ise, sonuç sayısal bir dizi olacaktır. Bazı öğeler sayılar olarak ayrıştırılamıyorsa, sayılar ve dizelerden oluşan heterojen bir dizi döndürülür.

# Örnekler

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = ["a"; "b"; "c"; "d"];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end;

julia> readdlm("delim_file.txt")
4×2 Matrix{Any}:
 1  "a"
 2  "b"
 3  "c"
 4  "d"

julia> rm("delim_file.txt")
```
