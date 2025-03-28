```
readchomp(x)
```

Lit l'intégralité de `x` en tant que chaîne et supprime une seule nouvelle ligne à la fin s'il y en a une. Équivalent à `chomp(read(x, String))`.

# Exemples

```jldoctest
julia> write("my_file.txt", "JuliaLang est une organisation GitHub.\nElle a de nombreux membres.\n");

julia> readchomp("my_file.txt")
"JuliaLang est une organisation GitHub.\nElle a de nombreux membres."

julia> rm("my_file.txt");
```
