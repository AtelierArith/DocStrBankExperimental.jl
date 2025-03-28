```
readchomp(x)
```

Liest den gesamten Inhalt von `x` als Zeichenfolge und entfernt eine einzelne abschließende neue Zeile, falls vorhanden. Entspricht `chomp(read(x, String))`.

# Beispiele

```jldoctest
julia> write("my_file.txt", "JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder.\n");

julia> readchomp("my_file.txt")
"JuliaLang ist eine GitHub-Organisation.\nEs hat viele Mitglieder."

julia> rm("my_file.txt");
```
