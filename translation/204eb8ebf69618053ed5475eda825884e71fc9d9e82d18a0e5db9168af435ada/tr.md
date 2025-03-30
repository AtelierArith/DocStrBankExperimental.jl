```
return
```

`return x`, verilen değeri `x` çağıranına geri göndererek kapsayıcı fonksiyonun erken çıkmasına neden olur. Değer olmadan `return` kullanmak, `return nothing` ile eşdeğerdir (bkz. [`nothing`](@ref)).

```julia
function compare(a, b)
    a == b && return "equal to"
    a < b ? "less than" : "greater than"
end
```

Genel olarak, bir `return` ifadesini bir fonksiyon gövdesinin herhangi bir yerine, derinlemesine iç içe döngüler veya koşullar içinde yerleştirebilirsiniz, ancak `do` blokları ile dikkatli olun. Örneğin:

```julia
function test1(xs)
    for x in xs
        iseven(x) && return 2x
    end
end

function test2(xs)
    map(xs) do x
        iseven(x) && return 2x
        x
    end
end
```

İlk örnekte, `return` bir çift sayı ile karşılaştığında `test1`'den çıkış yapar, bu nedenle `test1([5,6,7])` `12` döner.

İkinci örneğin aynı şekilde davranmasını bekleyebilirsiniz, ancak aslında oradaki `return` yalnızca *içteki* fonksiyondan ( `do` bloğu içindeki) çıkış yapar ve bir değer `map`'e geri verir. `test2([5,6,7])` ardından `[5,12,7]` döner.

Üst düzey bir ifadede (yani herhangi bir fonksiyonun dışında) kullanıldığında, `return` mevcut üst düzey ifadenin tamamının erken sona ermesine neden olur.
