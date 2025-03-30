```
swapfield!(value, name::Symbol, x, [order::Symbol])
swapfield!(value, i::Int, x, [order::Symbol])
```

Atomik olarak bir alanı aynı anda almak ve ayarlamak için işlemleri gerçekleştirin:

```
y = getfield(value, name)
setfield!(value, name, x)
return y
```

!!! uyum "Julia 1.7"
    Bu fonksiyon Julia 1.7 veya daha yenisini gerektirir.

