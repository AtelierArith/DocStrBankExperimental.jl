```
touch(path::AbstractString)
touch(fd::File)
```

Bir dosyanın son değiştirilme zamanını mevcut zamana günceller.

Eğer dosya mevcut değilse yeni bir dosya oluşturulur.

`path` döner.

# Örnekler

```julia-repl
julia> write("my_little_file", 2);

julia> mtime("my_little_file")
1.5273815391135583e9

julia> touch("my_little_file");

julia> mtime("my_little_file")
1.527381559163435e9
```

[`mtime`](@ref) fonksiyonunun `touch` ile değiştirildiğini görebiliriz.
