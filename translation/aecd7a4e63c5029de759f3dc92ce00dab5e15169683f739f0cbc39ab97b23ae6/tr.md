```
fld(x, y)
```

`x / y`'den küçük veya eşit en büyük tam sayı. `div(x, y, RoundDown)` ile eşdeğerdir.

Ayrıca bkz. [`div`](@ref), [`cld`](@ref), [`fld1`](@ref).

# Örnekler

```jldoctest
julia> fld(7.3, 5.5)
1.0

julia> fld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) ile eltip Int64:
 -2  -2  -1  -1  -1  0  0  0  1  1  1
```

`fld(x, y)`'nin, kayan nokta sayıların gerçek değerine dayalı olarak kesin doğru tabanlı yuvarlama uygulaması nedeniyle, sezgisel olmayan durumlar ortaya çıkabilir. Örneğin:

```jldoctest
julia> fld(6.0, 0.1)
59.0
julia> 6.0 / 0.1
60.0
julia> 6.0 / big(0.1)
59.99999999999999666933092612453056361837965690217069245739573412231113406246995
```

Burada olan, `0.1` olarak yazılan kayan nokta sayısının gerçek değerinin, sayısal değer 1/10'dan biraz daha büyük olmasıdır; oysa `6.0` sayısı tam olarak 6'yı temsil eder. Bu nedenle `6.0 / 0.1`'in gerçek değeri 60'tan biraz daha azdır. Bölme işlemi yapıldığında, bu tam olarak `60.0`'a yuvarlanır, ancak `fld(6.0, 0.1)` her zaman gerçek değerin tabanını alır, bu nedenle sonuç `59.0`'dır.
