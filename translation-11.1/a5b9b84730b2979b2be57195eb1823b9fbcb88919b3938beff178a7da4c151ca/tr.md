```
detect_ambiguities(mod1, mod2...; recursive=false,
                                  ambiguous_bottom=false,
                                  allowed_undefineds=nothing)
```

Belirtilen modüllerde tanımlı belirsiz yöntemlerin `(Method,Method)` çiftlerinden oluşan bir vektör döndürür. Tüm alt modüllerde test etmek için `recursive=true` kullanın.

`ambiguous_bottom`, yalnızca `Union{}` tür parametreleri tarafından tetiklenen belirsizliklerin dahil edilip edilmeyeceğini kontrol eder; çoğu durumda bunu `false` olarak ayarlamak isteyebilirsiniz. [`Base.isambiguous`](@ref) için bakın.

`allowed_undefineds` ile ilgili bir açıklama için [`Test.detect_unbound_args`](@ref) bakın.

!!! compat "Julia 1.8"
    `allowed_undefineds`, en az Julia 1.8 gerektirir.

