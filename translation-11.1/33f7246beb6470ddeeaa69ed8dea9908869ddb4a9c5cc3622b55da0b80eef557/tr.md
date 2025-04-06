```
parse(tip, str; taban)
```

Bir dizeyi sayı olarak ayrıştırır. `Tam Sayı` türleri için bir taban belirtilebilir (varsayılan 10'dur). Kesirli sayı türleri için dize ondalık kesirli bir sayı olarak ayrıştırılır. `Karmaşık` türler, istenen türde `Complex(R,I)` olarak `"R±Iim"` biçimindeki ondalık dizelerden ayrıştırılır; `"i"` veya `"j"` de `"im"` yerine kullanılabilir ve `"R"` veya `"Iim"` de geçerlidir. Dize geçerli bir sayı içermiyorsa, bir hata oluşur.

!!! uyumluluk "Julia 1.1"
    `parse(Bool, str)` en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> parse(Int, "1234")
1234

julia> parse(Int, "1234", base = 5)
194

julia> parse(Int, "afc", base = 16)
2812

julia> parse(Float64, "1.2e-3")
0.0012

julia> parse(Complex{Float64}, "3.2e-1 + 4.5im")
0.32 + 4.5im
```
