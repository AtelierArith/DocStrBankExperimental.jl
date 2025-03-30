```
mkpath(path::AbstractString; mode::Unsigned = 0o777)
```

Gerekli olduğu gibi `path` içindeki tüm ara dizinleri oluşturur. Dizinler, varsayılan olarak `0o777` olan ve mevcut dosya oluşturma maskesi tarafından değiştirilen `mode` izinleriyle oluşturulur. [`mkdir`](@ref) ile karşılaştırıldığında, `mkpath`, `path` (veya onun parçaları) zaten mevcutsa hata vermez. Ancak, `path` (veya onun parçaları) mevcut bir dosyaya işaret ediyorsa bir hata fırlatılacaktır. `path`'i döndürür.

Eğer `path` bir dosya adı içeriyorsa, bir dizin oluşturmak için dosya adını kullanmaktan kaçınmak için muhtemelen `mkpath(dirname(path))` kullanmak isteyeceksiniz.

# Örnekler

```julia-repl
julia> cd(mktempdir())

julia> mkpath("my/test/dir") # üç dizin oluşturur
"my/test/dir"

julia> readdir()
1-element Array{String,1}:
 "my"

julia> cd("my")

julia> readdir()
1-element Array{String,1}:
 "test"

julia> readdir("test")
1-element Array{String,1}:
 "dir"

julia> mkpath("intermediate_dir/actually_a_directory.txt") # iki dizin oluşturur
"intermediate_dir/actually_a_directory.txt"

julia> isdir("intermediate_dir/actually_a_directory.txt")
true

```
