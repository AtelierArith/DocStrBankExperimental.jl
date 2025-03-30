```
//(num, den)
```

İki tam sayıyı veya rasyonel sayıyı bölerek [`Rational`](@ref) sonucu verir. Daha genel olarak, `//` tam sayı veya rasyonel bileşenlere sahip diğer sayısal türlerin tam rasyonel bölümü için kullanılabilir; örneğin, tam sayı bileşenlerine sahip karmaşık sayılar.

`//` ile kayan nokta ([`AbstractFloat`](@ref)) argümanlarına izin verilmediğini unutmayın (değerler rasyonel olsa bile). Argümanlar [`Integer`](@ref), `Rational` veya bunların bileşenleri olan alt türler olmalıdır.

# Örnekler

```jldoctest
julia> 3 // 5
3//5

julia> (3 // 5) // (2 // 1)
3//10

julia> (1+2im) // (3+4im)
11//25 + 2//25*im

julia> 1.0 // 2
HATA: MethodError: no method matching //(::Float64, ::Int64)
[...]
```
