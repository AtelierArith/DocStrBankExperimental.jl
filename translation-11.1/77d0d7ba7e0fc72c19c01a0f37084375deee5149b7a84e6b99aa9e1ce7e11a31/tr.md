```
mutable struct
```

`mutable struct`, [`struct`](@ref) ile benzer, ancak ayrıca türün alanlarının inşaattan sonra ayarlanmasına izin verir.

Bir mutable struct'ın bireysel alanları, onları değişmez hale getirmek için `const` olarak işaretlenebilir:

```julia
mutable struct Baz
    a::Int
    const b::Float64
end
```

!!! compat "Julia 1.8"
    Mutable struct'ların alanları için `const` anahtar kelimesi en az Julia 1.8 gerektirir.


Daha fazla bilgi için [Bileşik Türler](@ref) bölümüne bakın.
