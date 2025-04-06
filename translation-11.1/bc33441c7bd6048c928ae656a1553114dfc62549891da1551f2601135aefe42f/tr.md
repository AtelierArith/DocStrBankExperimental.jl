```
homedir() -> String
```

Mevcut kullanıcının ana dizinini döndürür.

!!! not
    `homedir`, ana dizini `libuv`'nin `uv_os_homedir` aracılığıyla belirler. Ana dizini ortam değişkenleri aracılığıyla nasıl belirleyeceğinizle ilgili ayrıntılar için [`uv_os_homedir` belgelerine](http://docs.libuv.org/en/v1.x/misc.html#c.uv_os_homedir) bakın.


Ayrıca bkz. [`Sys.username`](@ref).
