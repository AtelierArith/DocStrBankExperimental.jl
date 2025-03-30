```
@threadcall((cfunc, clib), rettype, (argtypes...), argvals...)
```

`@threadcall` makrosu, [`ccall`](@ref) ile aynı şekilde çağrılır, ancak işi farklı bir iş parçacığında yapar. Bu, mevcut `julia` iş parçacığının engellenmeden bir engelleyici C fonksiyonunu çağırmak istediğinizde yararlıdır. Eşzamanlılık, libuv iş parçacığı havuzunun boyutuyla sınırlıdır; varsayılan olarak 4 iş parçacığıdır, ancak `UV_THREADPOOL_SIZE` ortam değişkenini ayarlayarak ve `julia` sürecini yeniden başlatarak artırılabilir.

Çağrılan fonksiyonun asla Julia'ya geri çağrıda bulunmaması gerektiğini unutmayın.
