```
factorial(n::Integer)
```

`n`'nin faktöriyeli. Eğer `n` bir [`Integer`](@ref) ise, faktöriyel en az 64 bit'e yükseltilmiş bir tam sayı olarak hesaplanır. `n` küçük değilse bu taşma yapabilir, ancak sonucu tam olarak hesaplamak için `factorial(big(n))` kullanabilirsiniz.

Ayrıca [`binomial`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> factorial(6)
720

julia> factorial(21)
HATA: OverflowError: 21, tabloda bakmak için çok büyük; bunun yerine `factorial(big(21))` kullanmayı düşünün
Stacktrace:
[...]

julia> factorial(big(21))
51090942171709440000
```

# Dış bağlantılar

  * [Faktöriyel](https://en.wikipedia.org/wiki/Factorial) Wikipedia'da.

```
