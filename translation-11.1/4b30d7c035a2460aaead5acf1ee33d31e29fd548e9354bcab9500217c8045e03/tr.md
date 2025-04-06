```
AbstractIrrational <: Real
```

Tam sayısı, diğer sayısal miktarlarla yapılan aritmetik işlemlerde doğru hassasiyete otomatik olarak yuvarlanan tam bir irrasyonel değeri temsil eder.

`MyIrrational <: AbstractIrrational` alt türleri en azından `==(::MyIrrational, ::MyIrrational)`, `hash(x::MyIrrational, h::UInt)` ve `convert(::Type{F}, x::MyIrrational) where {F <: Union{BigFloat,Float32,Float64}}` işlevlerini uygulamalıdır.

Bir alt tür, zaman zaman rasyonel değerleri temsil etmek için kullanılıyorsa (örneğin, `√n` için tam sayılar `n` olduğunda bir karekök türü, `n` bir mükemmel kare olduğunda rasyonel bir sonuç verecektir), o zaman `isinteger`, `iszero`, `isone` ve `==` işlevlerini `Real` değerleri ile uygulamalıdır (çünkü bunların hepsi `AbstractIrrational` türleri için varsayılan olarak `false` döner), ayrıca [`hash`](@ref) işlevini karşılık gelen `Rational` ile eşit olacak şekilde tanımlamalıdır.
