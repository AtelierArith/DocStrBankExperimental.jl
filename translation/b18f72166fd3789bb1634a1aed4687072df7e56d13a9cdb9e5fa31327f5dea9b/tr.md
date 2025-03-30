```
range(start, stop, length)
range(start, stop; length, step)
range(start; length, stop, step)
range(;start, length, stop, step)
```

Argümanlardan eşit aralıklı elemanlarla ve optimize edilmiş depolama ile özel bir dizi (bir [`AbstractRange`](@ref)) oluşturun. Matematiksel olarak bir aralık, `start`, `step`, `stop` ve `length`'in herhangi üçü ile benzersiz bir şekilde belirlenir. Geçerli `range` çağrıları şunlardır:

  * `start`, `step`, `stop`, `length`'in herhangi üçü ile `range` çağrısı yapın.
  * `start`, `stop`, `length`'in iki tanesi ile `range` çağrısı yapın. Bu durumda `step` bir olarak varsayılacaktır. Her iki argüman da Tam Sayı ise, bir [`UnitRange`](@ref) döndürülecektir.
  * `stop` veya `length`'in bir tanesi ile `range` çağrısı yapın. `start` ve `step` bir olarak varsayılacaktır.

Dönülen tür hakkında ek bilgiler için Genişletilmiş Yardım'a bakın. Ayrıca logaritmik olarak aralıklı noktalar için [`logrange`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> range(1, length=100)
1:100

julia> range(1, stop=100)
1:100

julia> range(1, step=5, length=100)
1:5:496

julia> range(1, step=5, stop=100)
1:5:96

julia> range(1, 10, length=101)
1.0:0.09:10.0

julia> range(1, 100, step=5)
1:5:96

julia> range(stop=10, length=5)
6:10

julia> range(stop=10, step=1, length=5)
6:1:10

julia> range(start=1, step=1, stop=10)
1:1:10

julia> range(; length = 10)
Base.OneTo(10)

julia> range(; stop = 6)
Base.OneTo(6)

julia> range(; stop = 6.5)
1.0:1.0:6.0
```

Eğer `length` belirtilmemişse ve `stop - start` bir tam sayı katı değilse, `stop`'dan önce biten bir aralık üretilecektir.

```jldoctest
julia> range(1, 3.5, step=2)
1.0:2.0:3.0
```

Ara değerlerin rasyonel olarak hesaplanmasını sağlamak için özel önlemler alınmıştır. Bu neden olduğu aşırı yükten kaçınmak için [`LinRange`](@ref) yapıcısına bakın.

!!! uyumluluk "Julia 1.1"
    `stop` bir konum argümanı olarak en az Julia 1.1 gerektirir.


!!! uyumluluk "Julia 1.7"
    Anahtar kelime argümanları olmadan ve `start` bir anahtar kelime argümanı olarak en az Julia 1.7 gerektirir.


!!! uyumluluk "Julia 1.8"
    `stop` yalnızca bir anahtar kelime argümanı olarak veya `length` yalnızca bir anahtar kelime argümanı olarak gerektiren sürümler en az Julia 1.8 gerektirir.


# Genişletilmiş Yardım

`range`, argümanlar Tam Sayı olduğunda bir `Base.OneTo` üretecektir ve

  * Sadece `length` sağlandığında
  * Sadece `stop` sağlandığında

`range`, argümanlar Tam Sayı olduğunda bir `UnitRange` üretecektir ve

  * Sadece `start` ve `stop` sağlandığında
  * Sadece `length` ve `stop` sağlandığında

Bir `UnitRange`, `step` sağlandığında, bir olarak belirtilse bile üretilmez.
