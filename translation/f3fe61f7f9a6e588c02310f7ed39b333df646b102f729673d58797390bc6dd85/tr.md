```
f ∘ g
```

Fonksiyonları birleştirin: yani `(f ∘ g)(args...; kwargs...)` demek `f(g(args...; kwargs...))` anlamına gelir. `∘` sembolü Julia REPL'inde (ve uygun şekilde yapılandırılmış çoğu editörde) `\circ<tab>` yazarak girilebilir.

Fonksiyon birleştirmesi ön ek biçiminde de çalışır: `∘(f, g)` `f ∘ g` ile aynıdır. Ön ek biçimi birden fazla fonksiyonun birleştirilmesini destekler: `∘(f, g, h) = f ∘ g ∘ h` ve bir iterable fonksiyon koleksiyonunu birleştirmek için `∘(fs...)`. `∘`'ye verilen son argüman ilk önce çalıştırılır.

!!! compat "Julia 1.4"
    Birden fazla fonksiyon birleştirmesi en az Julia 1.4 gerektirir.


!!! compat "Julia 1.5"
    Tek bir fonksiyonun birleştirilmesi ∘(f) en az Julia 1.5 gerektirir.


!!! compat "Julia 1.7"
    Anahtar kelime argümanlarının kullanılması en az Julia 1.7 gerektirir.


# Örnekler

```jldoctest
julia> map(uppercase∘first, ["apple", "banana", "carrot"])
3-element Vector{Char}:
 'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)
 'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
 'C': ASCII/Unicode U+0043 (category Lu: Letter, uppercase)

julia> (==(6)∘length).(["apple", "banana", "carrot"])
3-element BitVector:
 0
 1
 1

julia> fs = [
           x -> 2x
           x -> x-1
           x -> x/2
           x -> x+1
       ];

julia> ∘(fs...)(3)
2.0
```

Ayrıca [`ComposedFunction`](@ref), [`!f::Function`](@ref) bakın.
