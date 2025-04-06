```
Threads.Condition([lock])
```

[`Base.Condition`](@ref) için thread güvenli bir versiyon.

Bir `Threads.Condition` üzerinde [`wait`](@ref) veya [`notify`](@ref) çağırmak için önce ona [`lock`](@ref) çağırmalısınız. `wait` çağrıldığında, kilit atomik olarak bloklama sırasında serbest bırakılır ve `wait` döndüğünde yeniden edinilecektir. Bu nedenle, bir `Threads.Condition` `c` kullanımı aşağıdaki gibi görünmelidir:

```
lock(c)
try
    while !thing_we_are_waiting_for
        wait(c)
    end
finally
    unlock(c)
end
```

!!! compat "Julia 1.2"
    Bu işlevsellik en az Julia 1.2'yi gerektirir.

