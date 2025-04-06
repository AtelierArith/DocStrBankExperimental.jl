```
Threads.threadid() -> Int
```

Geçerli yürütme ipliğinin kimlik numarasını alır. Ana iplik `1` kimliğine sahiptir.

# Örnekler

```julia-repl
julia> Threads.threadid()
1

julia> Threads.@threads for i in 1:4
          println(Threads.threadid())
       end
4
2
5
4
```

!!! not
    Bir görevin çalıştığı iplik, görev verirse değişebilir; bu duruma [`Görev Göçü`](@ref man-task-migration) denir. Bu nedenle, çoğu durumda `threadid()`'yi bir tampon veya durum nesneleri vektörüne indekslemek için kullanmak güvenli değildir.

