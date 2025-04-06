```
!f::Function
```

Predikat fonksiyonun olumsuzlanması: `!`'nin argümanı bir fonksiyon olduğunda, `f`'nin boolean olumsuzlamasını hesaplayan bir bileşik fonksiyon döndürür.

Ayrıca bkz. [`∘`](@ref).

# Örnekler

```jldoctest
julia> str = "∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"
"∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"

julia> filter(isletter, str)
"εδxyδfxfyε"

julia> filter(!isletter, str)
"∀  > 0, ∃  > 0: |-| <  ⇒ |()-()| < "
```

!!! uyumluluk "Julia 1.9"
    Julia 1.9 ile birlikte, `!f` bir [`ComposedFunction`](@ref) döndürür, anonim bir fonksiyon yerine.

