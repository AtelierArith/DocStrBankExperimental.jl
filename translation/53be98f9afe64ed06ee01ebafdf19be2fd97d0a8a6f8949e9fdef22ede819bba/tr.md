```
reset(::Event)
```

Bir [`Event`](@ref) nesnesini ayarlanmamış bir duruma geri döndürür. Daha sonra `wait` çağrıları, [`notify`](@ref) tekrar çağrılana kadar engellenecektir.
