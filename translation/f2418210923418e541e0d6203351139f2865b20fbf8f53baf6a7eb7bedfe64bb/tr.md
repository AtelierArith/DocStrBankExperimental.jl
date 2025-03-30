```
errno([kod])
```

C kütüphanesinin `errno` değerini alır. Bir argüman belirtilirse, `errno` değerini ayarlamak için kullanılır.

`errno` değerinin geçerliliği, yalnızca onu ayarlayan bir C kütüphanesi rutinine yapılan bir `ccall`'dan hemen sonradır. Özellikle, bir REPL'deki bir sonraki istemde `errno`'yu çağırmak mümkün değildir, çünkü istemler arasında birçok kod çalıştırılır.
