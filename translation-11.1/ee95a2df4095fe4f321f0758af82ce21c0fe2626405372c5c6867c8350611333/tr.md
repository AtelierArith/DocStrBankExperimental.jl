```
ndigits(n::Integer; base::Integer=10, pad::Integer=1)
```

Tam sayısı `n`'nin `base` tabanında yazıldığında kaç basamak olduğunu hesaplar (`base` değeri `[-1, 0, 1]` içinde olmamalıdır), isteğe bağlı olarak belirtilen boyuta sıfırlarla doldurulabilir (sonuç asla `pad`'den az olmayacaktır).

Ayrıca [`digits`](@ref), [`count_ones`](@ref) bakınız.

# Örnekler

```jldoctest
julia> ndigits(0)
1

julia> ndigits(12345)
5

julia> ndigits(1022, base=16)
3

julia> string(1022, base=16)
"3fe"

julia> ndigits(123, pad=5)
5

julia> ndigits(-123)
3
```
