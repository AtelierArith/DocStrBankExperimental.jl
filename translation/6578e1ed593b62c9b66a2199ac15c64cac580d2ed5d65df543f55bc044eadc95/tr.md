```
artifact_exists(hash::SHA1; honor_overrides::Bool=true)
```

Verilen artefaktın (sha1 git ağaç hash'i ile tanımlanan) disk üzerinde var olup olmadığını döndürür. Verilen artefaktın birden fazla konumda (örneğin, birden fazla depo içinde) mevcut olabileceğini unutmayın.

!!! compat "Julia 1.3"
    Bu fonksiyon en az Julia 1.3 gerektirir.

