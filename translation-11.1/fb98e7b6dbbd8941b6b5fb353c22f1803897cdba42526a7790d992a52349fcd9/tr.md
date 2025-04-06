```
@uint128_str str
```

`str`'yi [`UInt128`](@ref) olarak ayrıştırın. Dize geçerli bir tam sayı değilse bir `ArgumentError` fırlatın.

# Örnekler

```
julia> uint128"123456789123"
0x00000000000000000000001cbe991a83

julia> uint128"-123456789123"
HATA: LoadError: ArgumentError: "-123456789123" içinde geçersiz taban 10 rakamı '-'
[...]
```
