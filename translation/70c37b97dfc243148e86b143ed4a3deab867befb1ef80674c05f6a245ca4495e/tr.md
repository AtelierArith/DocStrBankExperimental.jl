```
stacktrace([trace::Vector{Ptr{Cvoid}},] [c_funcs::Bool=false]) -> StackTrace
```

Bir `StackFrame` vektörü biçiminde bir yığın izini döndürür. (Varsayılan olarak, stacktrace C işlevlerini döndürmez, ancak bu etkinleştirilebilir.) Bir iz belirtmeden çağrıldığında, `stacktrace` önce `backtrace` çağrısını yapar.
