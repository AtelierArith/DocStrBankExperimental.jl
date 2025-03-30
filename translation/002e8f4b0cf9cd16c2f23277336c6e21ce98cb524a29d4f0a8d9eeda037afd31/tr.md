```
unsafe_swap!(p::Ptr{T}, x, [order::Symbol])
```

Bu atomik olarak bir bellek adresini aynı anda almak ve ayarlamak için işlemleri gerçekleştirir. Donanım tarafından destekleniyorsa, bu uygun donanım talimatına optimize edilebilir, aksi takdirde yürütülmesi aşağıdaki gibi olacaktır:

```
y = unsafe_load(p)
unsafe_store!(p, x)
return y
```

Bu işlevdeki `unsafe` öneki, `p` işaretçisinin geçerli olduğunu doğrulamak için hiçbir doğrulama yapılmadığını gösterir. C'de olduğu gibi, programcı, bu işlevi çağırırken referans verilen belleğin serbest bırakılmadığından veya çöp toplayıcı tarafından toplanmadığından emin olmaktan sorumludur. Yanlış kullanım programınızı segfault yapabilir.

!!! compat "Julia 1.10"
    Bu işlev en az Julia 1.10 gerektirir.


Ayrıca bakınız: [`swapproperty!`](@ref Base.swapproperty!), [`atomic`](@ref)
