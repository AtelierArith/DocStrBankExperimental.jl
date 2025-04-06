```
detect_unbound_args(mod1, mod2...; recursive=false, allowed_undefineds=nothing)
```

Bağlı olmayan tür parametrelerine sahip olabilecek `Method`lerin bir vektörünü döndürür. Tüm alt modüllerde test etmek için `recursive=true` kullanın.

Varsayılan olarak, herhangi bir tanımsız sembol bir uyarı tetikler. Bu uyarı, atlanabilecek bir `GlobalRef` koleksiyonu sağlayarak bastırılabilir. Örneğin, ayarlamak

```
allowed_undefineds = Set([GlobalRef(Base, :active_repl),
                          GlobalRef(Base, :active_repl_backend)])
```

`Base.active_repl` ve `Base.active_repl_backend` hakkında uyarıları bastırır.

!!! compat "Julia 1.8"
    `allowed_undefineds` en az Julia 1.8 gerektirir.

