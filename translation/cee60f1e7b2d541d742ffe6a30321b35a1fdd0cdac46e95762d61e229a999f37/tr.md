```
connect(path::AbstractString) -> PipeEndpoint
```

`path`'teki adlandırılmış boruya / UNIX alan soketine bağlanın.

!!! note
    Unix'te yol uzunluğu 92 ile 108 byte arasında bir yere sınırlıdır (bkz. `man unix`).

