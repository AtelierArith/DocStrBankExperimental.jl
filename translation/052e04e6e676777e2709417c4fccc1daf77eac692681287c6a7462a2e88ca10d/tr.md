```
@int128_str str
```

`str`'yi [`Int128`](@ref) olarak ayrıştırın. Dize geçerli bir tam sayı değilse bir `ArgumentError` fırlatın.

# Örnekler

```jldoctest
julia> int128"123456789123"
123456789123

julia> int128"123456789123.4"
HATA: LoadError: ArgumentError: "123456789123.4" içinde geçersiz taban 10 rakamı '.' 
[...]
```
