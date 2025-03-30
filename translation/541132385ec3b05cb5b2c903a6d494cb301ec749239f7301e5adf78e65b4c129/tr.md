```
walkdir(dir; topdown=true, follow_symlinks=false, onerror=throw)
```

Bir dizinin dizin ağacını dolaşan bir yineleyici döndürür. Yineleyici, `(rootpath, dirs, files)` içeren bir demet döndürür. Dizin ağacı yukarıdan aşağıya veya aşağıdan yukarıya gezilebilir. Eğer `walkdir` veya `stat` bir `IOError` ile karşılaşırsa, varsayılan olarak hatayı yeniden fırlatır. Özel bir hata işleme fonksiyonu `onerror` anahtar argümanı aracılığıyla sağlanabilir. `onerror`, bir `IOError` ile argüman olarak çağrılır.

Ayrıca bakınız: [`readdir`](@ref).

# Örnekler

```julia
for (root, dirs, files) in walkdir(".")
    println("Dizinler $root içinde")
    for dir in dirs
        println(joinpath(root, dir)) # dizinlere giden yol
    end
    println("Dosyalar $root içinde")
    for file in files
        println(joinpath(root, file)) # dosyalara giden yol
    end
end
```

```julia-repl
julia> mkpath("my/test/dir");

julia> itr = walkdir("my");

julia> (root, dirs, files) = first(itr)
("my", ["test"], String[])

julia> (root, dirs, files) = first(itr)
("my/test", ["dir"], String[])

julia> (root, dirs, files) = first(itr)
("my/test/dir", String[], String[])
```
