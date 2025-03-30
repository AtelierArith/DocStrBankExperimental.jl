```
lock(f::Function, lock)
```

`lock`'ı al, `lock` tutulurken `f`'yi çalıştır ve `f` döndüğünde `lock`'ı serbest bırak. Eğer `lock` başka bir görev/iş parçacığı tarafından zaten kilitlenmişse, kullanılabilir hale gelene kadar bekle.

Bu fonksiyon döndüğünde, `lock` serbest bırakılmıştır, bu yüzden çağıran kişi `unlock` yapmaya çalışmamalıdır.

Ayrıca bakınız: [`@lock`](@ref).

!!! compat "Julia 1.7"
    İkinci argüman olarak bir [`Channel`](@ref) kullanmak, Julia 1.7 veya daha yenisini gerektirir.

