```
open(fd::OS_HANDLE) -> IO
```

Bir ham dosya tanımlayıcısını alır, bunu Julia'ya özgü bir IO türü içinde sarar ve fd tutamağının mülkiyetini alır. Orijinal tutamağın mülkiyetini ele geçirmemek için `open(Libc.dup(fd))` çağrısını yapın.

!!! uyarı     Bunu, sistemin başka bir parçası tarafından zaten sahip olunan bir tutamakta çağırmayın.
