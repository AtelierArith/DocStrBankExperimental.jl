```
let
```

`let` blokları yeni bir katı kapsam oluşturur ve isteğe bağlı olarak yeni yerel bağlamalar tanıtır.

Diğer [kapsam yapıları](@ref man-scope-table) gibi, `let` blokları yeni tanıtılan yerel değişkenlerin erişilebilir olduğu kod bloğunu tanımlar. Ayrıca, sözdizimi, virgülle ayrılmış atamalar ve isteğe bağlı olarak `let` ile aynı satırda görünebilecek değişken adları için özel bir anlam taşır:

```julia
let var1 = value1, var2, var3 = value3
    code
end
```

Bu satırda tanıtılan değişkenler `let` bloğuna özgüdür ve atamalar sırayla değerlendirilir; her sağ taraf, soldaki isim dikkate alınmadan kapsamda değerlendirilir. Bu nedenle, `let x = x` gibi bir şey yazmak mantıklıdır, çünkü iki `x` değişkeni farklıdır ve soldaki taraf, dış kapsamdan gelen `x`'i yerel olarak gölgeler. Bu, yerel kapsamlar her girişte yeni yerel değişkenler oluşturduğundan, yararlı bir deyim olabilir, ancak bu yalnızca kapsamlarını aşan değişkenler için gözlemlenebilir. Yukarıdaki örnekteki `var2` gibi bir atama olmadan `let` değişkeni, henüz bir değere bağlanmamış yeni bir yerel değişken tanımlar.

Buna karşılık, [`begin`](@ref) blokları da birden fazla ifadeyi bir araya getirir, ancak kapsam tanıtmaz veya özel atama sözdizimine sahip değildir.

### Örnekler

Aşağıdaki işlevde, `map` tarafından üç kez iteratif olarak güncellenen tek bir `x` vardır. Döndürülen kapanışlar, o bir `x`'in son değerini referans alır:

```jldoctest
julia> function test_outer_x()
           x = 0
           map(1:3) do _
               x += 1
               return ()->x
           end
       end
test_outer_x (generic function with 1 method)

julia> [f() for f in test_outer_x()]
3-element Vector{Int64}:
 3
 3
 3
```

Ancak, yeni bir yerel değişken tanıtan bir `let` bloğu eklersek, her bir yinelemede yakalanan üç farklı değişkenle sonuçlanır, bu durumda aynı ismi (gölgeleme) kullanmayı seçmiş olsak bile.

```jldoctest
julia> function test_let_x()
           x = 0
           map(1:3) do _
               x += 1
               let x = x
                   return ()->x
               end
           end
       end
test_let_x (generic function with 1 method)

julia> [f() for f in test_let_x()]
3-element Vector{Int64}:
 1
 2
 3
```

Yeni yerel değişkenler tanıtan tüm kapsam yapıları, tekrar tekrar çalıştırıldığında bu şekilde davranır; `let`'in ayırt edici özelliği, aynı isimdeki dış değişkenleri gölgelerken yeni `local`'ları özlü bir şekilde tanımlama yeteneğidir. Örneğin, `do` işlevinin argümanını doğrudan kullanmak da benzer şekilde üç farklı değişkeni yakalar:

```jldoctest
julia> function test_do_x()
           map(1:3) do x
               return ()->x
           end
       end
test_do_x (generic function with 1 method)

julia> [f() for f in test_do_x()]
3-element Vector{Int64}:
 1
 2
 3
```
