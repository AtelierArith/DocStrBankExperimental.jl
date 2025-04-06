```
listen(path::AbstractString) -> PipeServer
```

Adlandırılmış bir boru / UNIX alan soketi oluşturun ve dinleyin.

!!! not
    Unix'te yol uzunluğu 92 ile 108 bayt arasında bir yere kadar sınırlıdır (bkz. `man unix`).

