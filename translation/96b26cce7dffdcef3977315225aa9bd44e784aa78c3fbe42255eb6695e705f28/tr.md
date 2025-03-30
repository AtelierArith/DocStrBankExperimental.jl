```
if/elseif/else
```

`if`/`elseif`/`else` koşullu değerlendirme yapar, bu da kodun belirli bölümlerinin bir boolean ifadenin değerine bağlı olarak değerlendirilip değerlendirilmeyeceği anlamına gelir. İşte `if`/`elseif`/`else` koşullu sözdiziminin anatomisi:

```julia
if x < y
    println("x y'den küçüktür")
elseif x > y
    println("x y'den büyüktür")
else
    println("x y'ye eşittir")
end
```

Eğer koşul ifadesi `x < y` doğruysa, o zaman ilgili blok değerlendirilir; aksi takdirde koşul ifadesi `x > y` değerlendirilir ve eğer bu doğruysa, ilgili blok değerlendirilir; eğer hiçbir ifade doğru değilse, `else` bloğu değerlendirilir. `elseif` ve `else` blokları isteğe bağlıdır ve istenildiği kadar `elseif` bloğu kullanılabilir.

Bazı diğer dillerin aksine, koşullar `Bool` türünde olmalıdır. Koşulların `Bool`'a dönüştürülebilir olması yeterli değildir.

```jldoctest
julia> if 1 end
HATA: TypeError: boolean bağlamında kullanılan non-boolean (Int64)
```
