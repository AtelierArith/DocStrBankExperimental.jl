```
ifelse(condition::Bool, x, y)
```

`condition` `true` ise `x` döner, aksi takdirde `y` döner. Bu, `?` veya `if`'ten farklıdır çünkü sıradan bir işlevdir, bu nedenle tüm argümanlar önce değerlendirilir. Bazı durumlarda, `if` ifadesi yerine `ifelse` kullanmak, üretilen kodda dalı ortadan kaldırabilir ve sıkı döngülerde daha yüksek performans sağlayabilir.

# Örnekler

```jldoctest
julia> ifelse(1 > 2, 1, 2)
2
```
