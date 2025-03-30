```
lookup(pointer::Ptr{Cvoid}) -> Vector{StackFrame}
```

Bir yürütme bağlamına (genellikle `backtrace` çağrısıyla oluşturulan) işaretçi verildiğinde, yığın çerçevesi bağlam bilgilerini arar. O noktada iç içe geçmiş tüm işlevler için çerçeve bilgilerini içeren bir dizi döner, en içteki işlev önce gelir.
