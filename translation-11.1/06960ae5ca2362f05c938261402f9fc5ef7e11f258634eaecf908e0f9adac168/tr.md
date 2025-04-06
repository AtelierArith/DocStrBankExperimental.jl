```
setenv(command::Cmd, env; dir)
```

Verilen `command`'ı çalıştırırken kullanılacak ortam değişkenlerini ayarlayın. `env`, ya string'leri string'lere eşleyen bir sözlük, ya `"var=val"` biçiminde bir string dizisi ya da sıfır veya daha fazla `"var"=>val` çift argümanı olabilir. Mevcut ortamı değiştirmek (yerine koymak yerine) için, `env`'yi `copy(ENV)` ile oluşturun ve ardından `env["var"]=val` olarak ayarlayın ya da [`addenv`](@ref) kullanın.

`dir` anahtar kelime argümanı, komut için bir çalışma dizini belirtmek için kullanılabilir. `dir`, `command` için zaten belirtilmemişse mevcut çalışma dizini olan varsayılan `dir`'ye ayarlanır.

Ayrıca bkz. [`Cmd`](@ref), [`addenv`](@ref), [`ENV`](@ref), [`pwd`](@ref).
