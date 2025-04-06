```
put!(c::Channel, v)
```

Kanal `c`'ye bir öğe `v` ekler. Kanal doluysa engeller.

Tamponlanmamış kanallar için, farklı bir görev tarafından [`take!`](@ref) gerçekleştirilene kadar engeller.

!!! uyumluluk "Julia 1.1"
    `v`, `put!` çağrıldığında kanalın türüne [`convert`](@ref) ile dönüştürülür.

