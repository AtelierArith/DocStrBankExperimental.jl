```
issuccess(F::LU; allowsingular = false)
```

Bir matrisin LU faktörizasyonunun başarılı olup olmadığını test eder. Varsayılan olarak, geçerli ancak sıralı eksik U faktörü üreten bir faktörizasyon başarısız olarak kabul edilir. Bu, `allowsingular = true` geçerek değiştirilebilir.

!!! compat "Julia 1.11"
    `allowsingular` anahtar argümanı Julia 1.11'de eklendi.


# Örnekler

```jldoctest
julia> F = lu([1 2; 1 2], check = false);

julia> issuccess(F)
false

julia> issuccess(F, allowsingular = true)
true
```
