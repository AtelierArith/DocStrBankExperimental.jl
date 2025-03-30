```
abspath(path::AbstractString, paths::AbstractString...) -> String
```

Bir dizi yolu, bunları birleştirerek ve gerekirse mevcut dizini ekleyerek mutlak bir yola dönüştürür. `abspath(joinpath(path, paths...))` ile eşdeğerdir.
