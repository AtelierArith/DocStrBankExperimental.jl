```
makro
```

`makro`, üretilen kodu bir programa eklemek için bir yöntem tanımlar. Bir makro, bir dizi argüman ifadesini döndürülen bir ifadeye eşler ve sonuçta elde edilen ifade, makronun çağrıldığı noktada programa doğrudan yerleştirilir. Makrolar, üretilen kodu [`eval`](@ref Main.eval) çağırmadan çalıştırmanın bir yoludur, çünkü üretilen kod, çevresindeki programın bir parçası haline gelir. Makro argümanları ifadeler, literal değerler ve semboller içerebilir. Makrolar, değişken sayıda argüman (varargs) için tanımlanabilir, ancak anahtar kelime argümanlarını kabul etmez. Her makro ayrıca, makronun çağrıldığı satır numarasını ve dosya adını içeren `__source__` argümanını ve makronun genişletildiği modülü belirten `__module__` argümanını da otomatik olarak alır.

Bir makro yazma hakkında daha fazla bilgi için [Metaprogramming](@ref) bölümüne bakın.

# Örnekler

```jldoctest
julia> makro sayhello(name)
           return :( println("Merhaba, ", $name, "!") )
       end
@sayhello (1 yöntemli makro)

julia> @sayhello "Charlie"
Merhaba, Charlie!

julia> makro saylots(x...)
           return :( println("De: ", $(x...)) )
       end
@saylots (1 yöntemli makro)

julia> @saylots "hey " "there " "friend"
De: hey there friend
```
