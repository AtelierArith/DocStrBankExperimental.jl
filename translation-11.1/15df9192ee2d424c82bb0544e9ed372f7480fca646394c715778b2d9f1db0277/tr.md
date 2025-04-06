```
unsafe_replace!(p::Ptr{T}, expected, desired,
               [success_order::Symbol[, fail_order::Symbol=success_order]]) -> (; old, success::Bool)
```

Bu atomik olarak, bir bellek adresini verilen bir değere almak ve koşullu olarak ayarlamak için işlemleri gerçekleştirir. Donanım tarafından destekleniyorsa, bu uygun donanım talimatına optimize edilebilir, aksi takdirde yürütülmesi aşağıdaki gibi olacaktır:

```
y = unsafe_load(p, fail_order)
ok = y === expected
if ok
    unsafe_store!(p, desired, success_order)
end
return (; old = y, success = ok)
```

Bu işlevdeki `unsafe` ön eki, `p` işaretçisinin geçerli olduğunu doğrulamak için herhangi bir doğrulama yapılmadığını gösterir. C'de olduğu gibi, programcı, bu işlevi çağırırken referans verilen belleğin serbest bırakılmadığından veya çöp toplayıcı tarafından toplanmadığından emin olmaktan sorumludur. Yanlış kullanım programınızı segfault yapabilir.

!!! compat "Julia 1.10"
    Bu işlev en az Julia 1.10 gerektirir.


Ayrıca bakınız: [`replaceproperty!`](@ref Base.replaceproperty!), [`atomic`](@ref)
