```
readchomp(x)
```

`x`'i bir dize olarak tamamen okuyun ve varsa tek bir son satır sonunu kaldırın. `chomp(read(x, String))` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> write("my_file.txt", "JuliaLang bir GitHub organizasyonudur.\nBirçok üyesi vardır.\n");

julia> readchomp("my_file.txt")
"JuliaLang bir GitHub organizasyonudur.\nBirçok üyesi vardır."

julia> rm("my_file.txt");
```
