```
chmod(path::AbstractString, mode::Integer; recursive::Bool=false)
```

`path`'in izin modunu `mode` olarak değiştirir. Sadece tam sayı `mode`'lar (örneğin `0o777`) şu anda desteklenmektedir. Eğer `recursive=true` ise ve yol bir dizin ise, o dizindeki tüm izinler yinelemeli olarak değiştirilecektir. `path`'i döndür.

!!! not
    Julia 1.6'dan önce, bu Windows'ta dosya sistemi ACL'lerini doğru bir şekilde manipüle edemiyordu, bu nedenle yalnızca dosyalardaki salt okunur bitlerini ayarlıyordu. Artık ACL'leri manipüle edebilmektedir.

