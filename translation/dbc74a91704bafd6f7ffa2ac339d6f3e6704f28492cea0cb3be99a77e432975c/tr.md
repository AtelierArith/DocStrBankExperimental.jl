```
unsafe_modify!(p::Ptr{T}, op, x, [order::Symbol]) -> Pair
```

Bu atomik olarak, `op` fonksiyonunu uyguladıktan sonra bir bellek adresini almak ve ayarlamak için işlemleri gerçekleştirir. Donanım tarafından destekleniyorsa (örneğin, atomik artırma), bu uygun donanım talimatına optimize edilebilir, aksi takdirde yürütülmesi aşağıdaki gibi olacaktır:

```
y = unsafe_load(p)
z = op(y, x)
unsafe_store!(p, z)
return y => z
```

Bu fonksiyondaki `unsafe` ön eki, `p` işaretçisinin geçerli olduğunu doğrulamak için herhangi bir doğrulama yapılmadığını gösterir. C'de olduğu gibi, programcı, bu fonksiyonu çağırırken referans verilen belleğin serbest bırakılmadığından veya çöp toplanmadığından emin olmaktan sorumludur. Yanlış kullanım programınızı segfault yapabilir.

!!! compat "Julia 1.10"
    Bu fonksiyon en az Julia 1.10 gerektirir.


Ayrıca bakınız: [`modifyproperty!`](@ref Base.modifyproperty!), [`atomic`](@ref)
