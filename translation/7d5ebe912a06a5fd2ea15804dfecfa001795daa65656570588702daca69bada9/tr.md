```
__precompile__(isprecompilable::Bool)
```

Bu fonksiyonu çağıran dosyanın ön derlenebilir olup olmadığını belirtir, varsayılan olarak `true`'dur. Bir modül veya dosya *güvenli bir şekilde* ön derlenebilir değilse, Julia'nın onu ön derlemeye çalışması durumunda bir hata fırlatmak için `__precompile__(false)` çağrısı yapmalıdır.
