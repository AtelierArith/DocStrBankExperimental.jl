```
mkfifo(path::AbstractString, [mode::Integer]) -> path
```

`path`'te bir FIFO özel dosyası (adlandırılmış boru) oluşturur. Başarı durumunda `path`'i olduğu gibi döndürür.

`mkfifo` yalnızca Unix platformlarında desteklenmektedir.

!!! compat "Julia 1.11"
    `mkfifo`, en az Julia 1.11 gerektirir.

