```
parse(str, start; greedy=true, raise=true, depwarn=true, filename="none")
```

İfade dizesini ayrıştır ve bir ifade döndür (bu daha sonra eval ile yürütme için geçirilebilir). `start`, ayrıştırmaya başlamak için `str` içindeki ilk karakterin kod birimi indeksidir (tüm dize dizinlemesi gibi, bunlar karakter indeksleri değildir). Eğer `greedy` `true` (varsayılan) ise, `parse` mümkün olduğunca fazla girdi tüketmeye çalışacaktır; aksi takdirde, geçerli bir ifadeyi ayrıştırdığı anda duracaktır. Tamamlanmamış ama başka türlü sözdizimsel olarak geçerli ifadeler `Expr(:incomplete, "(hata mesajı)")` döndürecektir. Eğer `raise` `true` (varsayılan) ise, tamamlanmamış ifadeler dışındaki sözdizim hataları bir hata oluşturacaktır. Eğer `raise` `false` ise, `parse` bir hata oluşturacak bir ifade döndürecektir. Eğer `depwarn` `false` ise, kullanım dışı uyarılar bastırılacaktır. `filename` argümanı, bir hata oluştuğunda tanılama bilgilerini görüntülemek için kullanılır.

```jldoctest
julia> Meta.parse("(α, β) = 3, 5", 1) # dize başlangıcı
(:((α, β) = (3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 1, greedy=false)
(:((α, β)), 9)

julia> Meta.parse("(α, β) = 3, 5", 16) # dize sonu
(nothing, 16)

julia> Meta.parse("(α, β) = 3, 5", 11) # 3'ün indeksi
(:((3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 11, greedy=false)
(3, 13)
```
