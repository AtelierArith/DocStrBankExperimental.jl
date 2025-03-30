```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

Atomik olarak `op` fonksiyonunu uyguladıktan sonra bir alanı almak ve ayarlamak için işlemleri gerçekleştirin.

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

Eğer donanım tarafından destekleniyorsa (örneğin, atomik artırma), bu uygun donanım talimatına optimize edilebilir, aksi takdirde bir döngü kullanacaktır.

!!! compat "Julia 1.7"
    Bu fonksiyon Julia 1.7 veya daha yenisini gerektirir.

