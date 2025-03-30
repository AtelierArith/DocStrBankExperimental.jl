```
normpath(path::AbstractString, paths::AbstractString...) -> String
```

Bir dizi yolu birleştirerek ve "." ve ".." girişlerini kaldırarak normalleştirilmiş bir yola dönüştürür. `normpath(joinpath(path, paths...))` ile eşdeğerdir.
