```
parse(str; raise=true, depwarn=true, filename="none")
```

İfadenin dizesini açgözlü bir şekilde ayrıştırır ve tek bir ifade döndürür. İlk ifadenin ardından ek karakterler varsa bir hata fırlatılır. `raise` `true` (varsayılan) ise, sözdizimi hataları bir hata fırlatır; aksi takdirde, `parse` bir hata fırlatacak bir ifade döndürür. `depwarn` `false` ise, kullanım dışı uyarılar bastırılacaktır. `filename` argümanı, bir hata fırlatıldığında tanılama bilgilerini görüntülemek için kullanılır.

```jldoctest; filter=r"(?<=Expr\(:error).*|(?<=Expr\(:incomplete).*"
julia> Meta.parse("x = 3")
:(x = 3)

julia> Meta.parse("1.0.2")
HATA: ParseError:
# Hata @ none:1:1
1.0.2
└──┘ ── geçersiz sayısal sabit
[...]

julia> Meta.parse("1.0.2"; raise = false)
:($(Expr(:error, "geçersiz sayısal sabit "1.0."")))

julia> Meta.parse("x = ")
:($(Expr(:incomplete, "tamamlanmamış: girdi sonu için erken son")))
```
