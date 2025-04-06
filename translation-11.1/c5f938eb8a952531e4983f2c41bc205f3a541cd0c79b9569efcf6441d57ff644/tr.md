```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

Bir [`IOBuffer`](@ref) okuma yapmaya ve yazma işlemlerini ekleyerek gerçekleştirmeye olanak tanır. Arama ve kısaltma desteklenmez. Mevcut yapıcılar için [`IOBuffer`](@ref) belgesine bakın. Eğer `data` verilirse, bir veri vektörü üzerinde çalışacak bir `PipeBuffer` oluşturur ve isteğe bağlı olarak, altındaki `Array`'in büyüyemeyeceği bir boyut belirtebilirsiniz.
